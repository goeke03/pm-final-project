# PRD & Prototype Sprint (Module 4)

## Pick & scope with MoSCoW
- **The “Now” feature I’m scoping (name + one-line core description):** Plain explainer for why income is asked and how it is used
- **My finalized Must-Haves (after overriding the AI):** The explanation sits on the income screen they already see, above the field, in the language that screen already uses, readable on a phone without opening another page.
The field label names the period: this month’s income, the month they are in. A label that only says “Income” leaves N-01 in place.
Two sentences, always visible. Why we ask: to set an instalment that fits the month they are in. How the number is used: it sizes that instalment, and it leaves the balance they owe unchanged. That is the answer to N-06 on this step.
One action still finishes the step. They type the figure and continue.
- **What I demoted from Must → Should/Won’t, and why:** none

## Generate your Simplified PRD
- **One thing my PRD makes explicit that a vague brief would have missed:** The big picture
Vision. On a short break, a shift-work consumer sees that we want this month’s income to size an instalment, and can enter it without fearing the number will be used against them.

Press release. A consumer in shift or variable work cannot pay the balance in full. They open the instalment journey on a break, reach the income question, and cannot tell whether we mean this month or a normal month. They close it and mean to come back. That is N-01. The same step is where N-06 stops: “I was scared to type the wrong number. What if they use it against me?” T-206 records the gap: no help text says why income is asked or how it is used. In the sample month, 2,862 variable-or-shift starters agreed at 41.6%, against 48.1% for a fixed salary, and 419 contacts (16.2%) were people calling to ask why income is asked.

The income screen now names the period in the label, “This month’s income,” and shows two sentences before the field: we ask so the instalment can fit the month they are in, and the number sizes that instalment without changing the balance they owe. They type one figure and continue. The screen does not ask for a usual month, does not open the document upload (853 journeys in T-201 never arrived), and does not promise a lower instalment or a shorter plan. The production read is the go bar already set: variable-or-shift agreement rate above 41.6%, with the 60-day no-miss hold at or above 77.5% for this segment and 81.0% overall (3,115 of 3,846). The 6.5 point gap to 48.1% stays the hypothesis for the wider income work, not a claim for this copy.

Success metrics. Primary: agreement rate for variable-or-shift starters, baseline 41.6% of 2,862. Go bar: above 41.6% after one journey month. Guardrail: no missed payment within 60 days, at or above 77.5% for this segment (sample miss rate 22.5%) and 81.0% overall. The prototype has no live cohort. Those two reads happen after one journey month plus 60 days. The HTML file is gated by the three evals in section 3.

2. The details
Story 1. As a consumer in shift or variable work who cannot pay the balance in full and is setting up a plan on a short break, I want the income field to ask for this month, so that I can answer before I close the journey.

The visible label is “This month’s income.”
The label is on screen when the income step paints. Nothing has to be tapped to reveal the period.
A second field for a normal or typical month is absent.
Story 2. As that same person, afraid a wrong number will be used against me, I want two sentences on why the figure is asked and how it is used, so that I can type it without calling.

Both sentences are visible above the field on first paint, on a 390px-wide screen, with no modal and no other page.
Sentence one: the instalment should fit the month they are in. Sentence two: the number sizes that instalment, and the balance owed does not change.
No phone number, no chat, no help-centre link. In the sample, 419 people called about why income is asked, at an average 11.8 minutes.
Story 3. As that person, I want to enter one figure and see that it was saved as this month’s income, so that I know the step is done and the balance is the same.

Continue with a valid figure opens the confirmation in the same file.
Confirmation echoes the figure and repeats that the balance does not change.
Confirmation shows no instalment amount, no term in months, no document upload, and no retention period.
Screens to build. Exactly three, in one HTML file. Prototype copy is English, the language of this case pack. A second language is not built.

Screen A, entry point. The moment they start the plan, before the income field.

BU Collection mark
One line: “Set up a plan for the balance you cannot pay in full.”
No balance amount, no instalment, no login
One button: “Continue”
Screen B, feature core. The income step.

Step label: “Income”
Field label: “This month’s income”
Euro marker on an empty field. No prefilled amount
Sentence 1, always visible: “We ask for this month’s income so the instalment can fit the month you are in.”
Sentence 2, always visible: “This number sizes that instalment. It does not change the balance you owe.”
One numeric field, an inline message area, one “Continue” button, and a back control to Screen A
Screen C, success. The step is saved. The plan is not offered here.

Heading: “This month’s income is saved”
Echo: “This month’s income: €{what they entered}”
Sentence 2 repeated, unchanged
No instalment, term, document upload, chat, or agent handoff
One button, “Back to income”, returning to Screen B with the figure still in the field
Functional requirements. Eight must-haves, each measurable in the file.

On Screen B first paint, both approved sentences are above the input, with zero taps to reveal them.
The visible field label is exactly “This month’s income.”
The explainer text matches the two approved sentences character for character. Any other sentence in that block fails the build.
At 390px, both sentences and the field are on the income screen without a dialog.
Continue on an empty, negative, or non-numeric field stays on Screen B, leaves both sentences visible, and shows “Enter this month’s income in euros.”
Continue on a number from 0 to 999,999.99 inclusive, at most two decimal places, opens Screen C and echoes that number.
Screen C contains the echoed figure and sentence 2, and contains none of: an instalment amount, a term in months, a retention duration, “lower payment”, “shorter plan”, or “used against”.
The file issues no network request and shows no login. Reloading starts again at Screen A.
Smart behaviors.

Situation	Outcome
Screen B paints
Label and both sentences are visible. The field is empty.
Continue with an empty field or letters
Stay on Screen B. Inline line: “Enter this month’s income in euros.” Both sentences stay.
Continue with a negative number
Same block. The figure is not saved.
Continue with 0
Open Screen C. Echo “This month’s income: €0.” Repeat sentence 2. Add no line about a short month or a smaller plan. A shift month can be thin.
Continue with 0.01 to 999,999.99
Open Screen C. Echo the number. Repeat sentence 2. Do not calculate an instalment.
More than two decimal places, or above 999,999.99
Stay on Screen B with the same inline line. Do not round into a saved figure.
Back from Screen B
Return to Screen A. Keep a typed draft for the return to Screen B.
Back from Screen C
Return to Screen B with the saved figure still in the field.
Explainer text outside the two approved sentences
Paint “We can’t show this explanation.” Leave the field usable. Do not write a replacement sentence.
Technical constraints. No external APIs, fonts, analytics, or model. No login or saved profile. One HTML file, plain JavaScript, copy stored as constants. No second locale, agent desktop, document upload, or instalment maths. No chat surface that could write a sentence outside the allow-list.

3. The logistics
Features out. A second field for a normal month. Any change to instalment maths, including the affordability check. Photo upload, file size, or skipping a document. The explainer on the agent screen. Chat, video, or a help-centre page. A retention period written for this prototype. Different copy for shift and salaried workers. A promise of a lower instalment or a shorter plan. A 60-day hold dashboard.

Also off these three screens: the thin-month clause, the pass-through counter, a privacy link, a field hint, and a repeat of the sentences on plan review. Plan review is not one of the three screens.

Edge cases. Empty, letters, or a pasted sentence are blocked, and both sentences stay. Zero is saved as this month’s income, with no cheaper-plan comfort. That comfort is how a short plan gets mistaken for the right answer (N-02) and how the 22.5% segment miss rate gets worse. A large number inside the cap is echoed with no judgement line, because a judgement line is the N-06 fear. Back from confirmation keeps the figure. Clearing it repeats the wiped-answer loss T-204 shows on another screen. What a missed payment means is unanswered here: 482 sample contacts asked that, and it is a different feature. The safety guard is an allow-list check before Screen B paints. A mismatch shows “We can’t show this explanation.” There is no model in the file.

Decision log.

Name the period in the label, and stop. “This month’s income” is the answer to N-01. A second box for a usual month would keep them on the break. The thin-month clause stays out, so the screen remains two sentences.
Confirmation saves the figure and restates the unchanged balance. It does not offer a plan. An instalment preview would be the affordability feature, and a lower or shorter offer would press on the 77.5% and 81.0% hold. This prototype cannot move the 41.6% rate by showing a plan. It can prove the person can pass the question.
Evals. The pack has no timed baseline and no comprehension score. These are build gates.

Accuracy. In 10 walkthroughs briefed as the shift-work persona, at least 9 of 10 say both: the figure wanted is this month, not a usual month, and the balance does not change. Gate: 90%.
Time on task. Median time from Screen B paint to Screen C paint, across those 10 walkthroughs, is 45 seconds or less. The budget is the break in N-01. The 11.8 minutes on the 419 “why income is asked” calls is the cost of the explanation being missing, not the target for this screen.
Safety triggers. Across empty, letters, 0, a mid-range number, a number over the cap, and a back-and-forth from Screen C, the page shows zero retention durations, zero instalment amounts, and zero promises of a lower payment or a shorter plan. Gate: 0. One forbidden phrase fails the build.

## Prompt-to-prototype sprint
- **Where did the prototype reveal a gap in my PRD logic? (what I had to update):** no time for iterations
- **My prototype: save Claude's HTML as prototype.html in 04-roadmap/, open it in your browser, and add a screenshot:** <section id="screen-a" data-screen="a">
  <h1>Set up a plan for the balance you cannot pay in full.</h1>
  <button class="go" id="to-income" type="button">Continue</button>
</section>

<section id="screen-b" data-screen="b" hidden>
  <button class="back" id="back-entry" type="button">Back</button>
  <p class="step">Income</p>
  <div class="explain" id="explain">
    <p data-explainer>We ask for this month’s income so the instalment can fit the month you are in.</p>
    <p data-explainer>This number sizes that instalment. It does not change the balance you owe.</p>
  </div>
  <label for="income">This month’s income</label>
  <div class="money">
    <span aria-hidden="true">€</span>
    <input id="income" name="income" type="text" inputmode="decimal" autocomplete="off" value="">
  </div>
  <p class="msg" id="msg" aria-live="polite"></p>
  <button class="go" id="save-income" type="button">Continue</button>
</section>

<section id="screen-c" data-screen="c" hidden>
  <h1>This month’s income is saved</h1>
  <p class="echo" id="echo"></p>
  <p data-explainer>This number sizes that instalment. It does not change the balance you owe.</p>
  <button class="back-income" id="back-income" type="button">Back to income</button>
</section>
