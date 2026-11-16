# Experimentation Plan (Module 5)

## Get your documents ready
- **From M3, your hypothesis sentence:** Based on N-01, a shift worker who closed the journey on a break because they did not know if income meant this month or a normal month, N-06 and T-206, where the income number is unexplained and feels unsafe to type, T-201, where 853 income documents never arrived, and a sample-month agreement rate of 41.6% for 2,862 variable or shift starters against 48.1% for a fixed salary, with 1,421 people leaving after the affordability questions and 1,313 at the income document, I believe that asking for the income of the month they are in, and telling them why that number is needed and how long it is kept, for consumers in shift or variable work who cannot pay in full, will result in more of them finishing a plan they are still paying 60 days later, as measured by a 6.5 percentage point rise in their agreement rate, from 41.6% to 48.1%. I will protect the share of new agreements with no missed payment within 60 days, 81.0% overall and 77.5% for this segment, and I will make a go/no-go decision after one journey month plus 60 days
- **From M3, your primary success metric & guardrail metric:** The agreement rate for variable-or-shift starters. The baseline is 41.6% on 2,862 starters. Fixed salary is 48.1%. It moves in the month of the journey, before the 60-day result, and it is the published gap for this consumer. Count it as the gap closing only while the guardrail holds. The overall agreement rate rose from 43.1% to 46.0% in the same months the hold got worse.
The share of new agreements with no missed payment within 60 days. It must not drop. The baseline is 81.0% (3,115 of 3,846). From the miss rates, the earlier months were 84.8%, 84.1%, and 84.4% while 12 months was shown first, then 81.6%, 81.2%, and 81.0% after the 6 month plan was shown first. For variable or shift income, the current hold is 77.5%, from the 22.5% miss rate. This is the book of plans that already pay.
- **From M4, the feature you scoped in your PRD this is what you're testing:** Plain explainer for why income is asked and how it is used

## Define your experiment parameters
- **Feature under test pull from your M4 PRD:** Plain explainer for why income is asked and how it is used
- **Persona pull your M2 persona:** Chat users match the whole movement. Of 1,497 starters who used the chat, 53.3% reach an agreement, 21.6% of those agreements miss a payment within 60 days, 27.1% contact an agent, and 41.5% finish in self-service. More agreements, more misses, less agent contact, more self-service.

Variable or shift income feels the missed payment most, without the extra agreements. Of 2,862 starters, 22.5% of agreements miss within 60 days, the highest miss rate in the file, and the agreement rate is 41.6%.

Two claims, and three or more, feel it as not getting a plan and needing a person. Two claims (2,130 starters): agreement 37.7%, agent contact 40.0%, miss 21.4%, self-service 26.0%, median instalment €88.73. Three or more (838): agreement 27.6%, agent contact 43.0%, miss 21.2%, self-service 19.3%, median instalment €114.84. One claim is the other side: agreement 52.1%, agent contact 25.6%, miss 18.1%, median instalment €58.72.

Fixed salary and income not given sit under the miss rate, at 17.4% and 17.7%. Portfolio type barely separates (purchased 19.4% miss, client collection 18.8%). Mobile is the volume, 6,563 starters, with a lower agreement rate (43.8% against 54.0% on desktop) and almost the same miss rate (18.9% against 19.2%). Of the entry channels, the letter QR code is the higher miss, at 20.3%.
- **Expected outcome the behaviour change you expect, from your M3 hypothesis:** Consumers whose income changes with the shift are asked, mid-break, for a single income figure they cannot place as this month or a normal month, so they leave the plan unfinished. Fewer of them reach an agreement (41.6% versus 48.1% on a fixed salary), more of those who do miss a payment within 60 days (22.5% versus 17.4%), and the agent who inherits the case cannot see the income answers already typed.
- **Primary success metric the one number that defines success, from M3:** The agreement rate for variable-or-shift starters. The baseline is 41.6% on 2,862 starters. Fixed salary is 48.1%. It moves in the month of the journey, before the 60-day result, and it is the published gap for this consumer. Count it as the gap closing only while the guardrail holds. The overall agreement rate rose from 43.1% to 46.0% in the same months the hold got worse.
- **Baseline rate today's rate of your primary metric, from your M3 data:** The agreement rate for variable-or-shift starters. The baseline is 41.6% on 2,862 starters. Fixed salary is 48.1%. It moves in the month of the journey, before the 60-day result, and it is the published gap for this consumer. Count it as the gap closing only while the guardrail holds. The overall agreement rate rose from 43.1% to 46.0% in the same months the hold got worse.
- **Guardrail metric & boundary what must not break, and how far it can move before you investigate:** From the miss rates, the earlier months were 84.8%, 84.1%, and 84.4% while 12 months was shown first, then 81.6%, 81.2%, and 81.0% after the 6 month plan was shown first. For variable or shift income, the current hold is 77.5%, from the 22.5% miss rate. This is the book of plans that already pay.
- **Minimum Detectable Effect (MDE) the smallest improvement worth shipping, your floor:** 2%
- **Sample size per arm use the calculator in the builder, baseline + MDE:** 1000
- **Traffic split & test duration 50/50 standard · cover ≥ 2 weekly cycles:** 50/50 standard · cover ≥ 2 weekly cycles
- **Significance threshold p < 0.05 is standard, explain any deviation:** p < 0.05

## Define your control and variant
- **Control (A) the current experience, reference your M2 moment of misery and M3 funnel/workflow data:** _(not filled in)_
- **Variant (B) your single change, copy the relevant screens & functional requirements from your M4 PRD:** _(not filled in)_
- **Isolation check, what has NOT changed? list everything identical between arms (app version, eligibility rules, notifications, onboarding). If something changed inadvertently, your test is compromised.:** _(not filled in)_

## Formalize your hypothesis & shipping criteria
- **Your hypothesis (filled in):** We will SHIP if the agreement rate for variable-or-shift starters improves by ≥ 2 percentage points at two-sided p < 0.05 and the 60-day no-miss hold for this segment does not fall below 77.5%, and does not fall below the control arm, after 9 months from the start.

We will ITERATE if the agreement rate is higher than control, the lift is below 2 percentage points, and the hold is still at or above 77.5% and at or above control.

We will KILL if the agreement rate shows no improvement or moves negatively, or if the hold falls below 77.5% or below control.

The read date is fixed at the end of those 9 months. No results are reviewed before this date.

Intake is the first 7 sample-months. That segment produces 2,862 starters in a sample month, about 1,430 per arm, and a 2-point lift at 80% power needs about 9,600 per arm. The single read is 60 days after intake closes, which is the first date the hold can be scored. A 14-day peek cannot see a 2-point lift or a 60-day miss.
- **Your shipping criteria (filled in):** We will SHIP if the agreement rate for variable-or-shift starters improves by ≥ 2 percentage points at two-sided p < 0.05 and the 60-day no-miss hold for this segment does not fall below 77.5%, and does not fall below the control arm, after 9 months from the start.

We will ITERATE if the agreement rate is higher than control, the lift is below 2 percentage points, and the hold is still at or above 77.5% and at or above control.

We will KILL if the agreement rate shows no improvement or moves negatively, or if the hold falls below 77.5% or below control.

The read date is fixed at the end of those 9 months. No results are reviewed before this date.

Intake is the first 7 sample-months. That segment produces 2,862 starters in a sample month, about 1,430 per arm, and a 2-point lift at 80% power needs about 9,600 per arm. The single read is 60 days after intake closes, which is the first date the hold can be scored. A 14-day peek cannot see a 2-point lift or a 60-day miss.
- **Hardest parameter to define, and did it change your hypothesis? quick debrief:** The hardest parameter to define is the size of the lift you require before you ship, the minimum detectable effect.

Every other blank was already in the file or falls out of arithmetic. The persona and the feature were scoped. The agreement rate and the 60-day hold each have a baseline: 41.6% of 2,862 variable-or-shift starters, and a 77.5% no-miss hold. p < 0.05 is a convention. Once you pick a 2 percentage-point lift and 80% power, the duration is just volume: about 9,600 starters per arm, about 7 sample-months of intake, then 60 days so the hold exists.

The 2 points are not in the file. The only gap this consumer owns is 6.5 points, from 41.6% up to the fixed-salary rate of 48.1%. That is the whole distance between shift income and a salary. Two sentences on one screen do not come with a measured share of those 6.5 points. The funnel cannot supply it either: 1,421 people leave after the affordability questions, and the pack does not say how many of them are variable-or-shift, or how many would have reached an agreement if the label had named the month.

That choice also sets the risk. A lift of about 3 points in overall agreement, from 43.1% to 46.0%, is already in the file, and it arrived with the hold falling from 84.8% to 81.0%. A 2-point bar sits inside a move the book has already paid for. A 6.5-point bar would shrink the test to about 900 people per arm and would claim a result this copy cannot own.
