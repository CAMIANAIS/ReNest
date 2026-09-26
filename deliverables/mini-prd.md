# ReNest Mini-PRD — Camila Mamani

> ReNest is a local marketplace for second-hand furniture. This document is a mini-PRD (Product Requirements Document) that explains the problem, the features and the MVP, and it is for designers, devs and QA.

## Glossary

| Term | What it means |
|------|---------------|
| North Star | The main metric for the whole ReNest app |
| L2   | A smaller, more specific metric that helps the North Star go up |
| Guardrail | A metric that must not get worse while we push the North Star up. If it crosses its threshold, we pause and investigate. |
| MVP (Minimum Viable Product) | The smallest version of the product we can launch, so users can try it and we get feedback |
| Non-functional requirement | How well the app works, e.g. speed, or how many minutes it takes to update |

## Problem Frame (from Day 1)

* Problem statement: Buyers cannot tell an item's condition from its photos, so they do not contact sellers. As a result, listings go stale and buyers leave the app.
  * Photos don't show condition → buyers don't contact sellers → listings go stale → buyers leave
* **Persona**
  * **Snapshot**
    * Greg, 29
    * Car salesperson
    * Lives in Delaware
    * Setting up his living room with quirky furniture
    * Browses at night on his computer
  * **Key pain:** anxious about receiving furniture that doesn't match the pictures.
* North Star Metric: monthly successful transactions (the buyer and seller mark the item as sold in the app, and the buyer confirms pickup)
* Value proposition: For quirky-furniture buyers who can't tell if photos match reality, ReNest gives high-quality, real photos, so buyers don't waste their day off searching elsewhere.

## Goals & success metrics

* **North Star:** monthly successful transactions (the buyer and seller mark the item as sold in the app, and the buyer confirms pickup)
* **L2 (supporting signal):** view → contact rate, the % of buyers who send a first message after viewing a listing.
  * Why: if buyers don't trust the pictures, they don't contact the seller. When trust goes up, this rate goes up first, before transactions.
* **Guardrail 1:** photo-match %. It must stay at or above 90%. If transactions go up but photo-match drops below 90%, sellers may be gaming the photos (hiding scratches with angles, or using old photos). Then we pause and investigate.

▎ 📝 Assumption: 90% is a starting guess. We will change it after we get real feedback.

* **Guardrail 2:** listing completion rate, the % of sellers who start a listing and publish it. It should not drop more than 10 points from the baseline.
  * Why: the 5-photo rule and the damage photo slot add complexity for the seller. If sellers quit, buyers see fewer listings and transactions go down.

    > ❓ Open question: can ReNest see when a deal is completed? If payment and pickup happen offline, how can we know it happened? If not, we may need a "Mark as sold" step in the app.
  * > 📝 **Assumption:** A transaction counts when the seller marks the item as sold and the buyer confirms pickup in the app. We assume that if the seller marks it as sold, they already did the transaction (payment).
    >
    > ⚠️ **Risk:** if users forget to click "Mark as sold" it would be undercounted transactions. Feature #10 (reminder, Next) helps with this. For the MVP, we accept undercounting.

## Candidate features (5–8) ← you'll prioritize these tomorrow

| \#  | Feature | Type | How it helps  | Roadmap |
|-----|---------|------|---------------|---------|
| 1   | 5-photo rule: front, back, left, right, panoramic, each at least 1600px | Greg | Shows all sides of the item | Now     |
| 2   | "Did the item match the photos?" yes/no survey after the deal | Measuring | Not directly. Helps find Photo-match %, the guardrail | Now     |
| 3   | Seller photo-match score (e.g. "9 of 10 buyers said the photos matched") | Greg | Greg can trust the quality of a seller's photos, based on past buyers | Next    |
| 4   | Extra photo slot for scratches and damage | Greg | Greg sees the real condition, scratches and damage included, before he contacts the seller | Now     |
| 5   | 360° video of the item | Greg | Greg sees how the item looks from every angle | Later   |
| 6   | In-person inspection checklist | Greg | When Greg picks up the item, he has a list of things to check | Cut     |
| 7   | "Ask for more photos" button | Greg | An easy way to tell the seller "I'm interested, but I want to see more photos" | Next    |
| 8   | "Photos taken on" date on listings | Greg | Greg knows the photos are not old | Now     |
| 9   | “Mark as sold” | Measuring | Not directly. Helps ReNest count the North Star. | Now     |
| 10  | Reminder of “Mark as sold” | Measuring | Not directly. Helps ReNest count the North Star. | Next    |

> 📝 10 candidates instead of 8: #9 and #10 are about counting the North Star
>
> * Tomorrow's prioritization will cut the list

## Sample requirements (pick 2–3 features)

Feature: 5-photo rule

* Functional: the system does not let a seller publish a listing with fewer than 5 photos (front, back, left, right, panoramic), each at least 1600px wide. Smaller photos are rejected.
* Functional: the system resizes photos wider than 1600px down to 1600px, so they load faster.
* Non-functional: the full batch of 5 photos finishes uploading within 10 seconds on a standard 4G connection.

Feature: Seller photo-match score

* Functional: the score (e.g. "9 of 10 buyers said the photos matched") shows next to the seller information, on the listing page and on the listing preview.
* Functional: the score updates each time a buyer answers the "did the item match the photos?" survey.
* Functional: sellers with no completed sales show a "New seller" badge instead of a score.
* Non-functional: the score updates within 1 minute after a buyer answers the survey.

Feature: Extra photo slot for scratches and damage

* Functional: after the 5 required photos, the seller must either add at least 1 photo labeled “Scratches and damage” or say “No visible damage”.
* Functional: the listing preview (search results) shows a small "Damage shown" or "No damage declared" label, so buyers can compare without opening each listing.
* Non-functional: the "Scratches & damage" section loads within 2 seconds on 4G.

Feature: “Photos taken on" date on listings

* Functional: the listing shows "Photos taken on [month, year]," using the capture date stored in the photo file (EXIF data).
* Functional: if any photo has no capture date, the listing shows "Photo date unknown" instead of a date. The listing is never blocked.
* Functional: if the oldest photo is more than 6 months older than the listing date, the listing shows "Some photos are older than 6 months."
* Non-functional: the date is read from the photo on the device before resizing, because resizing can remove it.

  > ❓ **Open question:** EXIF dates can be edited or removed. Check with devs whether they're reliable enough to show. If not, move #8 to Next and replace it with photos taken in the ReNest camera, which the app can date itself.

## MVP hypothesis

* In (smallest slice that delivers value): 5-photo rule (#1), "did it match the photos?" survey (#2), extra photo slot for scratches and damage (#4), "photos taken on" date (#8), "Mark as sold" + pickup confirmation (#9).

  > ❓ **Open question:** the 5-photo rule and the scratch photo slot may make sellers quit. Sellers may not want to show damage. We need to find out.
  >
  > ❓ **Open question:** photo dates can be removed or faked. Check with devs if #8 can be trusted.
  * Why: #1, #4 and #8 help Greg trust the photos *before* he contacts the seller, which is the problem. #4 and #8 also block the ways sellers can game photos (hiding scratches, using old photos). #2 measures the guardrail now and collects the data the seller score needs later.

    \#9 lets us count the North Star. The reminder (#10) is out for now, so we accept some undercounting.
* Out (explicitly, and why):
  * #3 Seller photo-match score: on launch day there are no sales yet, so every seller would show "New seller."
  * #5 360° video: too hard for now, for sellers and for devs.
  * #6 In-person inspection checklist: cut, low reach and low impact, only buyers at pickup. 
  * #7 "Ask for more photos" button: Greg can already message the seller to ask.
  * #10 "Mark as sold" reminder: deferred to Next, low RICE. It's cheap and the undercounting risk shows early, so it comes right after launch.

## Rough roadmap, Now / Next / Later

* Now (MVP): 5-photo rule, "did it match the photos?" survey, extra photo slot for scratches and damage, "photos taken on" date,"Mark as sold" + pickup confirmation.
* Next: seller photo-match score (once the survey has data), "Ask for more photos" button,"Mark as sold" reminder.

  > 💡 **Recommendation:** we recommend building the survey first, so the seller photo-match score has data when it launches.
* Later: 360° video (too hard for now), in-app payments,.
* Cut: in-person inspection checklist (low reach and low impact, only buyers at pickup)

  


---

  
Note from a teammate: The North Star defines a successful transaction as one where the buyer pays and picks up the item. How will ReNest confirm that both happened?  Clarifying this would help the team calculate its North Star metric.


Hi, thanks for the note! I changed the North Star: a transaction counts when the seller marks the item as sold and the buyer confirms pickup in the app. We assume that if the seller marks it as sold, they already did the transaction (payment). In-app payments are too big for the MVP, so we left them for later.