# ReNest Prioritization & Confirmed MVP — Camila Mamani

> ReNest is a local second-hand furniture marketplace. This doc shows how I prioritized ReNest features and which ones go in the MVP. It is for designers, devs and QA.

## Glossary

| Term | What it means |
| ---- | ------------- |
| RICE | A way to score features on 4 factors: Reach (how many users it reaches), Impact, Confidence (in %) and Effort (in person-weeks). Score = (R × I × C) ÷ E |
| Person-week | The work one person does in one week. Effort 2 = 1 dev for 2 weeks, or 2 devs for 1 week |
| MoSCoW | A way to sort features into what the MVP Must have, Should have, Could have and Won't have (for now) |
| Quick win | A feature with high value and low effort. Do these first |
| Big bet | A feature with high value and high effort. It can make sense to bet on it, but deliberately, maybe later |
| Money pit | A feature with low value and high effort. Avoid it |
| Orphan | A feature that doesn't move the North Star or any important metric, so we defer or cut it |
| North Star, L2, Guardrail | See the glossary in the mini-PRD |

## 1. RICE scores

Impact: 3 massive · 2 high · 1 med · 0.5 low · 0.25 min. Confidence as %. Effort in person-weeks. Reach from 1 to 10 (relative, no real data yet).

> 📝 **Assumption:** Reach is a guess, because ReNest has no real data yet.
>
> 💡 **Recommendation:** we recommend re-checking Confidence after the first month of data.

| #   | Feature | Reach | Impact | Confidence | Effort | RICE = (R×I×C)/E | Rank |
| --- | ------- | ----- | ------ | ---------- | ------ | ---------------- | ---- |
| 1   | 5-photo rule | 10 | 2 | 80% | 2 | 8 | 2 |
| 2   | "Did the item match the photos?" survey | 5 | 0.5 | 50% | 1 | 1.25 | 6 |
| 3   | Seller photo-match score | 2 | 2 | 50% | 3 | 0.67 | 9 |
| 4   | Extra photo slot for scratches and damage | 10 | 3 | 50% | 1 | 15 | 1 |
| 5   | 360° video | 3 | 2 | 50% | 5 | 0.6 | 10 |
| 6   | In-person inspection checklist | 5 | 0.5 | 50% | 1 | 1.25 | 7 |
| 7   | "Ask for more photos" button | 8 | 0.5 | 50% | 1 | 2 | 5 |
| 8   | "Photos taken on" date | 10 | 2 | 50% | 2 | 5 | 3 |
| 9   | "Mark as sold" + pickup confirmation | 5 | 0.5 | 80% | 1 | 2 | 4 |
| 10  | "Mark as sold" reminder | 3 | 0.5 | 50% | 1 | 0.75 | 8 |

Why these numbers:

* #1: Reach 10, all buyers see photos and every seller uploads them. Impact 2, photos help trust but don't guarantee a sale. Confidence 80%, sellers might quit. Effort 2, upload, size check and resize.
* #2: Reach 5, only buyers who finished a deal. Impact 0.5, it only measures, it doesn't move sales. Confidence 50%, few buyers answer. Effort 1, small.
* #3: Reach 2, new sellers have no score at launch. Impact 2, builds trust from past buyers. Confidence 50%, it depends on the survey. Effort 3, collect, calculate and show the score.
* #4: Reach 10, every seller does it and all buyers see it. Impact 3, shows the real condition Greg worries about. Confidence 50%, sellers may lie and click "No visible damage" when there is damage. Reach stays 10 because the step is required. Effort 1, just one more slot, and it reuses the upload from #1.

  > ❓ **Open question:** sellers may click "No visible damage" when there is damage, so #4's Confidence is only 50%. Will buyers still trust it? We need to find out.

* #5: Reach 3, few sellers would upload a video. Impact 2, a video shows how the furniture looks in the space. Confidence 50%, many sellers wouldn't upload a video because it can be slow. Effort 5, video is hard.
* #6: Reach 5, only buyers who pick up. Impact 0.5, it helps after contact, not before. Confidence 50%, not sure buyers use it at pickup. Effort 1, just a list.
* #7: Reach 8, buyers see it before contact, but some buyers don't need more photos. Impact 0.5, Greg can already message the seller. Confidence 50%, not sure buyers use it. Effort 1, just a button.
* #8: Reach 10, every listing shows the date. Impact 2, old photos hide wear, but less than hidden scratches. Confidence 50%, dates can be faked. Effort 2, read the date on the device before resizing, plus the 6-month warning.
* #9: Reach 5, only completed deals. Impact 0.5, same as the survey, it only measures, it doesn't move sales. Confidence 80%, I'm fairly sure it only reaches completed deals and only measures (users might forget to click, but that affects the count, not these numbers). Effort 1, just two buttons. Note: RICE scores it low, but the North Star can't be counted without it, so it goes to Must in MoSCoW.
* #10: Reach 3, only people who forgot to click. Impact 0.5, same as #9. Confidence 50%, not sure sellers react to reminders. Effort 1, just a notification.

Ties broken by judgment. At 2 (#9, #7): #9 first, because the North Star depends on it. At 1.25 (#2, #6): #2 first because it gives data to the guardrail and to the seller photo-match score (#3), then #6.

## 2. MoSCoW (for the MVP)

* Must: #4 extra photo slot for scratches and damage, #1 5-photo rule, #9 "Mark as sold" + pickup confirmation. #4 and #1 solve the problem, #9 lets us count the North Star.
* Should: #8 "photos taken on" date, #2 survey (without it we can't check the guardrail, so we wouldn't know if sellers game the photos).
* Could: #10 "Mark as sold" reminder, #7 "Ask for more photos" button.
* Won't (now): #3 seller photo-match score, #5 360° video, #6 in-person inspection checklist.

## 3. Value vs. Effort

* Quick wins: #4, #1, #8 (#8 has the same effort as #1 but less value)
* Big bets: #5 360° video (high impact but high effort)
* Money pits (avoid): #3 seller photo-match score (small reach at launch, effort 3)
* Fill-ins (low value, low effort): #2, #6, #7, #10
* Not on the 2×2: #9. Like in RICE, it has low value, but it's a Must, because without it we can't count the North Star.

## 4. North Star check (no orphans)

| Feature | Metric it moves (NSM / supporting) | Keep / defer / cut |
| ------- | ---------------------------------- | ------------------ |
| #4 Extra photo slot for scratches and damage | L2 (view → contact rate). Risk: adds seller effort, watch Guardrail 2 | Keep |
| #1 5-photo rule | L2 (view → contact rate). Risk: adds seller effort, watch Guardrail 2 | Keep |
| #9 "Mark as sold" + pickup confirmation | North Star (it lets us count it) | Keep |
| #8 "Photos taken on" date | L2 (view → contact rate) | Keep |
| #2 Survey | Guardrail 1 (photo-match %) | Keep |
| #10 "Mark as sold" reminder | North Star (fewer undercounted transactions) | Defer to Next, low RICE |
| #7 "Ask for more photos" button | L2 (it's a kind of contact) | Defer to Next, Greg can already message |
| #6 In-person inspection checklist | North Star, a little (it can help close a deal at pickup) | Cut, low reach and low impact: only buyers at pickup |
| #3 Seller photo-match score | Guardrail 1 / L2 later, small reach at launch | Defer to Next, needs survey data |
| #5 360° video | L2, but small reach | Defer to Later, costs a lot |

## 5. Confirmed MVP

* In: #1 5-photo rule, #2 survey, #4 extra photo slot for scratches and damage, #8 "photos taken on" date, #9 "Mark as sold" + pickup confirmation.
* Out (and why):
  * #3 Seller photo-match score: deferred to Next, small reach at launch and it needs survey data.
  * #5 360° video: deferred to Later, it costs a lot and reaches few people.
  * #6 In-person inspection checklist: cut, low reach and low impact, only buyers at pickup.
  * #7 "Ask for more photos" button: deferred to Next, Greg can already message the seller.
  * #10 "Mark as sold" reminder: deferred to Next, low RICE.

    > 💡 **Recommendation:** build #10 right after launch, because it's cheap and the undercounting risk shows early.

* Changed since Tuesday (and why):
  * Added #9 "Mark as sold" + pickup confirmation, so we can count the North Star.
  * Numbers vs judgment: #7 ranked 5th on RICE, only because it's cheap and reaches many people. I trust my judgment here: Greg can already message the seller, so it stays out.
  * #9 scored low on RICE (2, it only measures), but it's a Must, because without it we can't count the North Star.

## 6. One defended call

Feature: #4 Extra photo slot for scratches and damage — **in, and ranked first**.

#4 is ranked first with only 50% confidence, because it has the highest impact (3): it shows the real condition Greg worries about, which is the problem. The risk is that sellers lie and click "No visible damage" when there is damage. I accept that risk, because Guardrail 1 catches it: if sellers lie, photo-match % drops, and we pause and investigate.

## Self-check ("Watch out for these")

* Fake precision: first, 9 of 10 features had exactly 50% confidence (only #1 had 80%). Then Confidence did almost nothing to the order. Re-checked with "how sure am I about Reach and Impact?": #9 → 80%, #8 and #4 stay 50%. Still 8 of 10 at 50%, so this is only a first fix.
* Everything is a "Must": avoided. Only 3 Musts (#4, #1, #9). The MVP has 5 features, because it also has 2 Shoulds (#8, #2).
* Prioritizing the feature you love: avoided. My gut said #1 was the most important, but #4 ranked first and I kept it first.
* Treating the score as the decision: avoided. I went against RICE twice: #9 is in with a low score (without it we can't count the North Star), and #7 is out with a higher score (Greg can already message the seller).
