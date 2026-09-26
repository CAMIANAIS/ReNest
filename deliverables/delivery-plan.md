# ReNest Delivery Plan — Camila Mamani

> ReNest is a local second-hand furniture marketplace. This doc makes the #1 MVP feature delivery-ready: what "done" means, the top risks, and the go / no-go call. It is for designers, devs and QA.

## Glossary

| Term | What it means |
|------|---------------|
| Acceptance criteria | The rules that say when a feature is done |
| Given / When / Then | A way to write acceptance criteria. Given = the starting situation, When = one action, Then = what you see |
| Happy / unhappy path | Happy = the feature works as expected. Unhappy = something goes wrong |
| L2 | A smaller, more specific metric that helps the North Star go up |
| Guardrail | A metric that must not get worse while we push the North Star up. If it crosses its threshold, we pause and investigate |
| Baseline | The number before launch (the last 4 weeks before launch) |
| Rollback | Turning the feature off |

## 1. Acceptance criteria

**Feature: #4 Extra photo slot for scratches and damage** (ranked first in the prioritization)

* **Happy path (damage photo):** *Given* the seller uploaded a damage photo, *when* Greg opens the listing, *then* the page shows the photo with a "Damage" label.
* **Happy path (no damage):** *Given* the seller chose "No visible damage", *when* Greg opens the listing, *then* the page shows the text "Seller says: no visible damage".
* **Unhappy path (step skipped):** *Given* the damage step is empty, *when* the seller taps "Publish", *then* publishing is blocked and the damage step is highlighted.

  > 🧩 **Assumption:** most sellers are honest when they choose "No visible damage". Guardrail 1 (photo-match %) checks this after launch.

## 2. Top 3 risks

| Risk | Type | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- | --- |
| Sellers lie and choose "No visible damage" when there is damage | Adoption | H | H | Accept + monitor: if photo-match % (Guardrail 1) drops below 90%, pause and investigate. |
| Sellers find the extra step annoying and don't publish | UX | M | H | Watch listing completion rate (Guardrail 2): if it drops more than 10 points from the baseline, simplify the step. |
| Photo upload fails on a slow phone connection | Technical | L | H | Reduce: test the upload on slow connections before launch. Low likelihood because #4 reuses the upload from #1. |

* Cut: "Greg gets scared by the Damage label." That's not a risk, it's the feature working: Greg skips a bad item, which is the problem we're solving.

  > ❓ **Open question:** photo-match % comes from the survey (#2). What if only a few buyers answer in the first 2 weeks? How many answers do we need before we trust the 90%?

## 3. Go / no-go

* **Ship criteria (what must be true):**
  * The 3 acceptance criteria pass in QA testing.
  * The upload is tested on a slow connection.
  * Guardrail tracking (photo-match % and listing completion rate) is ready on launch day.
* **Decision owner:** the PM, because they own the product. QA says if the criteria pass, and the dev lead says if the upload is ready.
* **Rollback trigger:** listing completion rate (Guardrail 2) drops more than 10 points below the baseline (the last 4 weeks before launch) for 2 weeks. Turning #4 off fixes sellers leaving. It does not fix lying (Greg would just get less truth), so lying means pause and investigate, not roll back.

  > 💡 **Recommendation:** start measuring listing completion rate 4 weeks before launch, so the baseline exists on launch day.
* **What we'll monitor:**
  * First 2 weeks: L2 (view → contact rate) goes up, and both guardrails stay stable. L2 moves first, because the North Star is only monthly.
  * After the first month: the North Star (monthly successful transactions) goes up.
* **Recommendation: GO**, if the ship criteria pass. #4 shows Greg the real damage before he contacts the seller, and the guardrails catch the risks.
