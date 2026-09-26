# ReNest Problem Frame — Camila Mamani

> ReNest is a local marketplace for second-hand furniture. This document frames the problem: who has it, how we measure success, and  the value for the user. It is for designers, devs and QA.

## Glossary

| Term | What it means |
|------|---------------|
| North Star | The main metric for the whole ReNest app |
| L2   | A smaller, more specific metric that helps the North Star go up |
| Guardrail | A metric that must not get worse while we push the North Star up. If it crosses its threshold, we pause and investigate. |
| JTBD(Job To Be  Done ) | What the user is trying to get done, in their words |

## 0. Problem vs. solution warm-up

Mark each ask P or S. Reframe solutions as problems.

| \#  | Ask | P / S | If S → reframed as a problem |
|-----|-----|-------|------------------------------|
| 1   | Add a five-star rating system for sellers. | S     | Buyers don't trust sellers, so they hesitate to contact them. |
| 2   | Buyers don't trust that listing photos reflect the item's real condition. | P     |                              |
| 3   | Let buyers filter listings by distance. | S     | Buyers don't want to travel far for an item, so they skip listings that are too far away. |
| 4   | Sellers don't know what price will actually make an item sell. | P     |                              |
| 5   | Add an in-app chat so buyers and sellers can message. | S     | Buyers and sellers have to share personal info to communicate, so they feel unsafe and hesitate to message. |
| 6   | New buyers land on the home screen and don't know where to start. | P     |                              |
| 7   | Put a "verified seller" badge on every profile. | S     | New sellers have no history to prove they're trustworthy, so buyers avoid buying from them. |
| 8   | Buyers message sellers and often never hear back. | P     |                              |
| 9   | Auto-reject blurry photos at upload. | S     | Buyers cannot see the item clearly from blurry photos, so they avoid contacting the seller. |
| 10  | Add a wishlist / save-for-later feature. | S     | Buyers forget about items they liked and lose track of them, so they lose interest and end up buying somewhere else. |

## 1. Problem statement (2–3 specific sentences)

What is the problem · who has it · why it matters.

> Buyers cannot tell an item's condition from its photos, so they do not contact sellers. As a result, listings go stale and buyers leave the app.

## 2. Primary persona

* Snapshot: Greg, 29, car salesperson, lives alone in Delaware, US, setting up his living room, his old furniture is worn out.
* Context: browses at night on his day off, on his computer.
* Goals: find quirky furniture that actually looks like it does in the pictures.
* Pains: feels anxious about receiving furniture that doesn't match the pictures.
* Current workaround: checks similar items on eBay or visits a local furniture store, can't find quirky pieces there either, so it feels like a waste of his only day off.
* The job (JTBD): "When I'm browsing a listing, I want to judge an item's real condition before I reach out, so I can make the buying decision easily."
* In their words: "I'm trying to find unique furniture that matches my apartment. When I'm browsing, I like the pictures, but I can't tell if it's really that good."

## 3. North Star Metric

* **North Star:** monthly successful transactions (the buyer and seller mark the item as sold in the app, and the buyer confirms pickup)
* **L2** (supports the North Star): view → contact rate, the % of buyers who send a first message after viewing a  listing.
* Why it reflects real user value (not a vanity number): It only counts real sales (both mark it as sold and the buyer confirms pickup), not people who download the app  and never buy.

  > 📝 Assumption callout: if the  seller marks it as sold, they already did the transaction  (payment).
* **Guardrail 1:** photo-match % must stay at or above 90%. If transactions go up but photo-match drops below 90%, it may mean sellers are gaming the photos (hiding scratches with angles, or using old photos). Then we pause and investigate. 

  > 📝 Assumption callout: The 90% is a starting guess; we will change it after we get real feedback.

**Guardrail 2:** listing completion rate, the % of sellers who start a listing and publish it. It should not  drop more than 10 points from the baseline

## 4. Value proposition (pain → gain)

What changes for the persona when this is solved.

> For quirky-furniture buyers who can't tell if photos match reality, ReNest shows 5 photos of every side, a photo of the damage, and the date the photos were taken, so buyers don't waste their day off searching elsewhere.