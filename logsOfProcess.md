# Practice notes — Day 1 (Problem Framing)

Working log of the reasoning, not the final answers. Final answers go in `problem-frame.md`.

## Warm-up: problem vs. solution (10 asks)

**#1 — "Add a five-star rating system for sellers."**
- First guess: solution ✅
- Why: a rating system is a feature. The real need under it is *trust* — buyers don't know if a seller is reliable.
- First reframe attempt accidentally repeated item #2's wording — caught and corrected.
- Second attempt smuggled the solution back in ("...so they need a rating system") — caught and corrected.
- Final reframe: "Buyers don't trust sellers, so they hesitate to contact them."

**First full pass (before double-checking):**
1 P, 2 P, 3 S, 4 P, 5 S, 6 P, 7 S, 8 P, 9 P, 10 S

**Two mistakes found on review:**
- #1 marked P, should be S (see above — it's the rating-system feature).
- #9 marked P, should be S — "Auto-reject blurry photos at upload" is a system action (a feature), not a problem statement.

**Corrected full pass:**
1 S, 2 P, 3 S, 4 P, 5 S, 6 P, 7 S, 8 P, 9 S, 10 S

**#9 reframe** — asked: what happens *to the buyer* because photos are blurry?
- Draft 1: "buyers dont look well at blurry photos so they dont buy" — too vague, "dont buy" isn't specific enough.
- Final: "Buyers cannot see the item clearly from blurry photos, so they avoid contacting the seller."

**Extra practice — reframed the remaining S's too (only 2 were required):**
- #3: "Buyers don't want to travel far for an item, so they skip listings that are too far away."
- #5: "Buyers and sellers have to share personal info to communicate, so they feel unsafe and hesitate to message."
- #7: "New sellers have no history to prove they're trustworthy, so buyers avoid buying from them." — noticed this is similar territory to #1 (trust) but distinct: #1 is about track record over time, #7 is about identity verification for brand-new sellers with no history yet.
- #10: "Buyers forget about items they liked and lose track of them, so they lose interest and end up buying somewhere else."

## Problem statement (step 3)

Started from the week's assigned problem quote:
> "Buyers can't tell whether a used item is worth contacting the seller about, so good listings go stale and buyers leave."

- Draft 1 drifted off-topic: talked about "trust" and "recently posted items" — not what the quote is about.
- Redirected back to the quote: the issue is buyers can't *judge* the item, not trust/timing.
- Draft 2: "buyers cant tell the item condition from photos so they dont contact sellers" — good, matches the core idea.
- Added the missing consequence (listings go stale, not just buyers leaving).
- Cleaned up from bullets/run-on into two real sentences.

**Final (also in problem-frame.md):**
> Buyers cannot tell an item's condition from its photos, so they do not contact sellers. As a result, listings go stale and buyers leave the app.

Noticed on our own that this final version reads close to the doc's own "Strong" example — checked with mentor, confirmed it's expected since both describe the same underlying problem, not a copy.

## Persona (step 4) — is this just copying Marta?

Worried the persona felt like a copy of Marta's example, since everyone works the same problem.
Clarified: the problem is shared on purpose — that part is expected to look similar for everyone.
What's unique is the specific person. Comparison:

| | Marta (doc example) | Greg (mine) |
|---|---|---|
| Wants | a decent sofa, fast, cheap | quirky/original pieces, worth paying fair price for |
| Worry | wasting a Saturday on a dud | receiving something that doesn't match the photo |
| Fallback today | checks Facebook Marketplace, asks a friend | eBay, local stores — can't find quirky stuff there either |
| Vibe | budget-conscious, practical | particular taste, hosts friends, cares about how his space looks |

Same lens (persona + JTBD + this problem), different person. Not a copy.

**Persona draft process — issues caught along the way:**
- First draft had a contradiction: "Industrial Engineer" in the snapshot vs. "car salesperson" in the description — fixed to car salesperson.
- Context, Current workaround, and "In their words" were missing from the first draft — required fields, easy to forget.
- Some Pains/Goals weren't tied to *this* problem (e.g. delivery timing, general dislike of retail) — cut, since they don't explain why Greg can't judge condition from photos.
- JTBD situation was "When I want some quirky furniture" (a desire, not a moment) — needs to be the moment he's stuck, e.g. "When I'm browsing a listing."
- Lots of flavor details (hiking, PlayStation nights, LED lights) don't explain the core problem — won't make the final 7-field version unless justified.

## North Star Metric (step 5)

- Draft 1: "Number of weekly active buyers completing their first purchase."
  - Issue: "first purchase" only covers new buyers — the photo-trust problem affects repeat buyers too.
  - Issue: full purchase completion is downstream of many other steps (price, meetup, payment), not just the photo/trust problem this week is about.
- Draft 2: "Weekly successful buyer-seller connections" — caught that this was word-for-word from the doc's own Strong example, not our own thinking. Rewrote to be specific to our problem.
- Draft 3: "Weekly listings where the seller replies and confirms it matches the photos."
- Why (not vanity): pushed to explain the mechanism, not just assert it —
  "Because a buyer already trusted the photos enough to reach out, a seller can only confirm a match if the item really is what the buyer expected. It can't go up while buyers still don't trust listings."

**Follow-up — how would you actually measure this?**
- Asked how the app would capture "confirms it matches" as data. Message roundtrips ruled out (more messages could mean a complaint, not a confirmation).
- Landed on: a post-deal rating/review is the trackable signal.
- Caught a subject mismatch: draft 3 said "seller confirms," but it's the *buyer* who judges whether the item matched — wrong actor.
- Raised a real concern: not every buyer leaves a review. Resolved: a North Star doesn't need 100% participation — a consistent sample is enough to trust the trend; boosting review rate is a separate problem for later.
- Intermediate: "Weekly deals where the buyer leaves a review confirming the picture looks like the actual furniture."

**Deeper dive — how ReNest would actually measure it:**
- Trigger: ask the buyer right after they mark a deal as done.
- The question needs to be specific, not a vague star rating: a yes/no "did the item match the photos?"
- Raw count vs. percentage: chose percentage, so growth in deal volume doesn't hide bad trust.
- Found a pasted external "metrics tree" (L1/L2/L3, GMV, 3D/AR rendering) that was far beyond this exercise's scope and not something built together — rejected it, since posting something you can't explain defeats the point. Used it as a chance to learn the difference between a company-wide North Star (e.g. GMV) and a problem-level success metric (this exercise's kind of "North Star") — this one is scoped to the single problem, not the whole business.

**Final:** North Star — `% of completed deals where the buyer answers "Yes" to "did the item match the photos?"` Why — "It can't rise if photos are misleading — and using a percentage (not a raw count) means it stays honest even as ReNest grows." (also updated in problem-frame.md)

## Value proposition (step 6)

- Draft 1 named "opportunity to ask the seller" as the change — caught that this isn't new, buyers can already message sellers today. The real change had to be about photo quality/trust, from the persona's own "needs and expectations" notes.
- Also mixed "buyers" (3rd person) with "you" (2nd person) — fixed to stay consistent.
- Final pronoun fix: "his" → "their" to match plural "buyers."

**Final:** "For quirky-furniture buyers who can't tell if photos match reality, ReNest gives high-quality, real photos, so buyers don't waste their day off searching elsewhere."

## North Star — "why" line was stale

- After updating the North Star to be buyer-centric, the "why it reflects real value" line still said "seller confirms" — leftover from the old wording, caused confusion when re-reading.
- Rewritten to match: "If buyers leave reviews confirming a match, the photos are accurate — this number can't go up while photos are misleading."
- Lesson: when one field changes, check the fields that reference it too.

---
## Final checklist (from the brief)
- [x] Problem statement is specific; names who and why (2–3 sentences)
- [x] Persona has context, goals, a concrete pain, and a current workaround — feels like one real person
- [x] North Star reflects value, not a vanity number
- [x] Value prop connects the pain to the gain

---
## Status: all sections complete
- Step 0: warm-up ✅
- Step 1: problem statement ✅
- Step 2: persona (Greg) ✅
- Step 3: North Star ✅
- Step 4: value proposition ✅

---
# Day 2–3 — Scoping, PRD & MVP (2026-09-23)

## Warm-up: problem statement from memory
- Recalled the first half ("buyers can't tell if a listing is worth contacting the seller") but forgot the consequence. Added it when asked: "good listings go stale and buyers leave."

## Metrics concepts (prep for mentorship)
- First guess: North Star = "a business goal." Corrected myself: North Star = **value for the user**. Money comes after, as a result.
- OMTM = the one metric to focus on *right now*; it can change later. ✅
- L1/L2/L3 first guess: "metrics for technical or marketing stuff." Real idea: they are **levels of a tree**. The top is the North Star; the smaller steps that feed it sit below.
- Mentor questions to ask: "Are the steps before my North Star my L2 metrics?" / "Is one persona enough, or should I add a seller persona?" / "Can I put Nerdery content in NotebookLM?"

## Requirements (Step 1 reading check)
- Functional = what the product does. Non-functional = how well it does it (performance, quality, constraints). ✅
- Quiz: "The listing page should feel trustworthy" — I called it non-functional. Trap: it's **not a requirement yet**, because QA can't test it.
- Rewriting it, step by step:
  - "listing page has all high quality pictures" → still vague ("high quality" = ?)
  - "at least 5 photos, from front, back, left, right, and panoramic" → testable ✅
  - Decided it's **functional**: the system doesn't let a seller publish with fewer than 5 photos.
- Fixing "high quality": first guess 540px ("regular quality"). Checked it against Greg's need instead of "what's normal". Mixed up angles (which sides) with pixels (how much detail) at first, then said "quality of furniture" (vague again). Made it concrete: scratches, stains, worn parts need detail.
- Decision: **at least 1600px**, so buyers can zoom in and see scratches.
- Tradeoff noticed: bigger photos load slower, so this can fight with a load-time NFR.
- Tradeoff to think about tomorrow: is a 5-photo rule bad for sellers? (Could make them drop off.)
- Keep for Step 5: *"The system does not let a seller publish a listing with fewer than 5 photos (front, back, left, right, panoramic), each at least 1600px."*

## Supporting signals (Step 3)
- Mapped Greg's path to the North Star: opens listing → looks at photos → contacts seller → **meets seller and sees item in person** → writes review. (Forgot the in-person step at first. You can't judge photo accuracy without seeing the item.)
- Signal 1: "% of buyers who contact a seller after viewing the photos." Almost the same as the brief's example, so I added a second one that fits our problem better.
- Signal 2: "% of buyers who buy after seeing the item in person." If photos were accurate, Greg buys.

## Status
- Step 1: reading ✅
- Step 2: frame copied into mini-PRD ✅
- Step 3: North Star + 2 signals ✅
- Steps 4–7: next

## Mentor feedback → North Star changed
- Mentor: the North Star must be **general**, for all of ReNest (like Airbnb = successful stays). My photo-accuracy metric is an **L2**, not the North Star. (The Day 1 session had pushed a problem-level North Star. That was wrong.)
- Choice: successful transactions vs 5-star ratings → **transactions**, because the examples count things that happen. Ratings also depend on people choosing to rate.
- Draft: "all delivered transactions including payment and delivery, per month" → caught a mismatch: ReNest doesn't deliver, Greg picks up the item in person.
- **New North Star:** monthly successful transactions (the buyer pays and picks up the item).
- Old North Star (% of deals where the buyer says the photos matched) moves down to L2.
- Found stale text myself (Day 1 lesson again): the Problem Frame in the PRD still had the old North Star, and so did `problem-frame.md` (already on Outline). Updated both, so my mentor sees the new one. Kept the old metric as L2 in `problem-frame.md`.
- The "why" line was stale too (it talked about photos and percentages). Rewrote it by comparing with a vanity number (downloads): "It only counts payments and item pickups, not people who just download the app and never buy."
- Re-checked the Day 1 checklist after the change. Vanity test ("could it go up while users get no real value?"): yes. Greg can pay and pick up a broken chair that the photos hid, and the North Star still goes up. My first reaction: "the North Star is not good."
- Learned: no single metric is perfect, and that's why PMs use a tree. A metric that catches the bad cases is a **guardrail**.
- Options: A) keep the general North Star and use the photo-match L2 as a guardrail, or B) put "matched the photos" inside the North Star. Chose **A**, because my mentor said the North Star must be general. Added a guardrail note to both deliverables.
- Picking the 2nd signal (the photo-match guardrail must be one of them). First pick: "buy after seeing the item," because it shows trust. Challenged: the problem statement says buyers "do not contact sellers." Switched to "contact after viewing photos." Then asked myself if I switched for a real reason or only because I was challenged. I confirmed it: **#1, because it measures the exact problem in my statement.**
- Final signals: photo-match % (L2/guardrail) + % of buyers who contact a seller after viewing the photos.

## Step 4 — Candidate features (in progress)
- #1 5-photo rule (1600px), from the requirements work.
- #2 Yes/no "did it match the photos?" survey after the deal. Also needed to measure the L2.
- "A lot of photos, more than expected" was the same as #1, so it counts once.
- "Listing relatively new": still open. What's the feature, and why does it help trust?
- Mentor tip: study competitors. On Facebook Marketplace I saw: (a) only one angle, and scratches not shown; (b) people judge seller profiles by the year they joined.
  - (b) is **seller** trust, a different problem. But seller reviews can fit if they're about photos. Chose a score over past buyers' photos, because it's easier to read → **#3 Seller photo-match score** (uses data from #2).
  - (a) First answer: "ask for a high quality picture". That's the same as #1 again. 5 good photos can still hide a scratch → **#4 Extra photo slot for scratches and damage**.
- "Being able to look at the whole furniture without hiding anything": a goal, not a feature. Asked: online or in person? → online → **#5 360° video of the item**.
- In-person step of Greg's chain: "a checklist app for checking the item in person." Not a separate app, it's one feature inside ReNest → **#6 In-person inspection checklist**.
- Used the unused steps of Greg's chain to reach 8:
  - "contacts seller" → **#7 "Ask for more photos" button**
  - Old idea "listing relatively new" → the real point is that old photos may not show the item today → **#8 "Photos taken on" date on listings**
- Step 4: 8 features ✅. Next: check that each one traces back to Greg's pain, then Step 5.

## Step 5 — Requirements
- Noticed: #6 (inspection checklist) is the weakest, because it helps *after* contact and the problem is about *before* contact. Not cut, since there's no filtering today. Note for tomorrow: #2 (survey) is also after the deal, but it feeds #3.
- Feature #1, first NFR draft was one long, polished paragraph ("shall allow up to 5 photos... resized to a maximum width of 1600px... within 10 seconds on 4G"). Problems:
  - It mixed functional and non-functional. Split it: upload/resize = functional; "5 photos within 10 seconds on 4G" = the real NFR.
  - Contradiction 1: "up to 5" vs "fewer than 5 can't publish" → fixed to 5.
  - Contradiction 2: "maximum 1600px" vs "at least 1600px". Asked what happens to a 1000px photo → rejected, so the rule is **at least**.
  - Kept the resize idea for photos that are too big: a 4000px photo gets resized down to 1600px so it loads faster. Both rules work together.

## Guardrail gets a number
- Brought a long guardrail text from research (a tool wrote most of it). Good idea inside: give the guardrail a number (90%).
- Checked the eBay claim ("≥99.5% dispute-free") against eBay's Seller Standards page. eBay says top sellers have **≤0.5% transaction defects**, so 99.5% is math from that, but it's "defect," not "dispute." The tool used the wrong word. Lesson: check sources before posting.
- "Gaming" in ReNest = hiding scratches with angles, or using old photos. Features #4 (scratch slot) and #8 ("photos taken on" date) block exactly those tricks.
- Why 90%? At first I repeated the tool's words ("reasoned starting assumption"). My real reason: it's a guess, and I'll change it after real feedback. Too high = false alarms; too low = we miss real problems.
- Final (my words): "Photo-match % must stay at or above 90%. If transactions go up but photo-match drops below 90%, it may mean sellers are gaming the photos (hiding scratches with angles, or using old photos). Then we pause and investigate. The 90% is a starting guess; we will change it after we get real feedback." Updated in both deliverables.
- Feature #3 (seller photo-match score), first draft: "somewhere visible in the UI next to seller information, even on the preview; updates as someone rates it." Kept "next to seller info" and dropped "somewhere visible" (too vague). Split it into 2 functional requirements.
- Added the NFR: the score updates **within 1 minute** after a survey answer.
- Edge case: a new seller has 0 sales → show a **"New seller" badge** instead of a score.
- Step 5 ✅: 2 features with requirements (5-photo rule, seller photo-match score).

## Step 6 — MVP hypothesis
- First pick: #1, #3, #4, "because they help Greg before contacting."
- Missed a dependency: #3 needs data from #2 → added #2 (now 4 features).
- Launch-day check: on day 1 nobody has sold anything, so every seller shows "New seller" → #3 moves to Next.
- Why keep #2 without #3? It measures the guardrail now and collects data for #3 later. One feature, two jobs.
- Out reasons: #3 no data yet; #5 too hard; #6 after contact. Forgot #7 and #8 at first.
- #8 moved **in**: it's easy and blocks old photos (connects to the guardrail). Note: photo dates can be removed or faked, so check with devs.
- #7 → Next: Greg can already message the seller to ask.
- **MVP: #1, #2, #4, #8.**

## Step 7 — Now / Next / Later
- Now = MVP (#1, #2, #4, #8). Next = #3, #7. #5 → Later (too hard).
- #6: first said Next with no reason, then Later "because it's not part of ReNest." That reason was wrong, since we agreed it's a feature inside ReNest. Went back to my Step 4 reason: **Later, because it helps after contact, not before.**
- Lesson: when I change an answer, the reason has to change too, not only the answer.

## Status: mini-PRD complete
- Steps 1–7 ✅. Next: run the "check yourself" list, post to Outline, tag my mentor, comment on a teammate's PRD.

## My mentor's feedback on the mini-PRD (iteration 2)
- **No content feedback.** 🎉 All the feedback was about formatting and communication:
  1. Add an intro (what ReNest is, what the doc is for, who it's for)
  2. Explain jargon (e.g. "Guardrail" → "Quality check", explain L2)
  3. Add "pieces of me": assumptions, open questions, recommendations
  4. Use tables and nested bullets
- Tip 1, intro: built it step by step. "Buyers of what?" → second-hand furniture, local. Audience: first said "stakeholders of the whole process of creation" → made it concrete: designers, devs and QA. Also explained "PRD" (tip 2 at the same time).
- Tip 2, jargon → chose a glossary table (it also covers tip 4). Terms: North Star, L2, Guardrail, MVP, Non-functional.
  - L2: first wrote "a technical metric". That's the same mistake as this morning (L1/L2/L3 = "technical or marketing"). Then "specific behaviour sub drivers", but "sub drivers" is jargon too. Final: "a smaller, more specific metric that helps the North Star go up."
  - Guardrail: first wrote "quality assurance policy", but QA means testing, which is a different thing. Final: "an alert that flags when something is wrong or suspicious."
  - MVP: first I only wrote the full name. That's not an explanation. Final: "the smallest version of the product we can launch, so users can try it and we get feedback."
- Tip 3, "pieces of me". New idea of my own: the scratch photo slot can make sellers leave, because sellers may not want to show damage.
  - Labels: 90% guess = assumption ✅; photo dates can be faked = open question ✅.
  - "5-photo rule may make sellers quit": first called it an assumption. Assumption = we believe it but didn't prove it; open question = we don't know yet. → **open question** (same for the scratch slot).
  - "Seller score needs survey data" is a fact, not advice → "**We recommend building the survey first.**"
  - Placement: each note goes next to the part it's about (guardrail, MVP, roadmap).
- Tip 4, formatting: turned the candidate features into a table (# / Feature / How it helps Greg / Roadmap). The "how it helps Greg" column also shows that every feature traces back to the problem.
  - #3: first wrote "increase trust on seller", but seller trust is a different problem → "trust the quality of a seller's photos."
  - #4: "reliable info about product" was vague → "sees the actual product with all he needs to consider" → made concrete: scratches and damage, before contact.

# Day 3–4 — PRD fixes & Prioritization (2026-09-24)

## Warm-up: problem from memory
- Recalled the chain: buyers don't trust photos → don't contact → listings go stale → buyers leave. For who: Greg, anxious the furniture won't match the pictures.

## Gut check: which feature moves the North Star most?
- First said #1 (5-photo rule), "Greg sees all sides." Chain: sees all sides → trusts → contacts → buys.
- Mentor asked if front/back/sides show **condition**. I switched to #4, then went back to #1 with a **new reason**: #4 could make sellers quit. Lesson: ReNest has two users. If sellers leave, Greg has nothing to buy.
- Why #1 is OK for sellers: "all angles is normal in any e-commerce." That's an **assumption**, not a fact (ReNest sellers are regular people, not shops).

## Critique from another AI → Goals & metrics rewrite
- Another AI rewrote my section. Rule: only add what I can explain.
  - L2 = view → contact rate. It goes up **before** transactions, because buyers contact first. This is a **leading indicator**.
  - 30% survey rule: only happy or angry buyers answer → **selection bias**.
  - Guardrail 2 = listing completion rate. Same idea I had myself (seller effort → sellers quit).
- Rewrote it in my own words. Mistakes I fixed: "if they wouldn't trust pictures they would contact" (logic reversed); Guardrail 2 had no "why"; the open question was written as a fact.
- Tip: ask other AIs for feedback, not rewrites.

## North Star changed (a teammate's comment)
- A teammate asked: how does ReNest confirm the buyer paid and picked up?
- New North Star: monthly successful transactions (the buyer and seller mark the item as sold in the app, and the buyer confirms pickup). Better because the app can **count** it.
- Payment: ReNest can't see cash. Chose to **assume** "Mark as sold" = paid. In-app payments are too big for the MVP → Later.
- Risk: users forget to click → transactions are **undercounted**. Idea: reminder notification → new feature.
- Found that the "Mark as sold" button itself wasn't in the feature list → added it. #9 = Mark as sold + pickup confirmation, #10 = reminder.
- Measuring features (#2, #9, #10) don't help Greg directly. Options: rename the column, two tables, or one table + a **Type** column (Greg / Measuring). Chose one table + Type, because it's simpler for devs.
- 10 candidates instead of 8: #9 and #10 are about counting the North Star, and prioritization cuts the list.
- Tried another AI's North Star (matched transactions via reviews, proxy, eBay reference). Too complex, and I couldn't defend it → went back to the simpler version. "Matched transactions" is a good Later idea.
- Source of truth = **Outline**. Too many local copies caused mistakes.
- Formatting: persona as nested bullets, problem as a one-line chain (A → B → C → D).

## Day 4 — RICE
- RICE = Reach, Impact, Confidence, Effort. Confidence keeps guesses honest: 50% confidence cuts the score in half, so **guesses rank lower**. (First calculation was wrong: I got B = 40. Redid it step by step: B = 10.)
- Mistakes I fixed while scoring:
  - #5: Reach 10 fought with Confidence 50% ("sellers could" vs "sellers won't") → Reach 3.
  - #6: Confidence 80% "because it's simple". That's Effort, not Confidence → 50%.
  - #7 and #10: copied the numbers from the row above. Thought again → different Reach.
  - #9: first gave Impact 3 "because the North Star depends on it", but I gave #2 0.5 because "it only measures". Both can't be true → Impact 0.5 in RICE, and #9 goes to **Must** in MoSCoW. A framework is a lens, not a verdict.
- Tie at 1.25 (#9, #2, #6) broken by judgment.
- Surprise: #7 ranked 4th only because it's cheap and reaches many people. RICE likes cheap things even when they don't matter much. Tuesday's reason still wins (Greg can already message).
- This morning my gut said #1 was most important. RICE put #4 first (Impact 3, Effort 1).

## Day 4 — MoSCoW, Value vs Effort, North Star check
- Must: #4, #1, #9. #7 in Should didn't match "Tuesday reason wins" → moved to Could. #2 in Could meant no way to check the guardrail → moved to Should.
- Value vs Effort: #1 and #8 have the same effort, so the difference is value → both quick wins. #5 = big bet (high impact, high effort). #3 = money pit for now.
- North Star check: #6 moves nothing → orphan, cut. "Cut" = never, "defer" = later → #3 and #5 are deferred (they're in the roadmap). #7 moves L2 (asking for photos is a kind of contact), not Guardrail 1.

## Status
## Step 6 — Confirmed MVP
- First answer flipped #2 and #10 against my own table (#2 out, #10 in). No new reason, so I went back: #2 stays (it protects Guardrail 1, low response was already in Confidence 50%), #10 out (low RICE).
- In: #1, #2, #4, #8, #9. Out: #3, #5, #7, #10 deferred, #6 cut. Changed since Tuesday: added #9.

## Step 7 — Defended call
- #9 in: low RICE, but no North Star without it. Trade-off: users might forget, the reminder is out, so we accept undercounting for now.

## Status
- Day 4 complete in `deliverables/prioritization.md`. Next: post to Outline, tag the mentor, comment on a teammate. Update the PRD MVP so #10 is out.

## Self-check ("Watch out for these")
- Fake precision: 8 of 10 at exactly 50% confidence. Removing it didn't change the order, so Confidence was doing nothing. Re-checked with "how sure am I about Reach and Impact?" → #9 80% (RICE 2, ties #7, #9 first by judgment). #8 stays 50% (fake dates make me *less* sure, not more).
- Musts: first said 6, but I was counting the MVP. Musts = 3 (#4, #1, #9).
- Feature I love (#1) ended 2nd. Went against RICE twice (#9 in, #7 out).

## Mentor formatting tips applied to prioritization.md
- Intro: first "for the mentor" → the real audience is designers, devs and QA, and it says what ReNest is.
- Glossary from memory: RICE, MoSCoW, quick win, big bet, money pit, orphan, person-week. Person-week: first "2 persons per week" → 1 person-week = the work one person does in one week (Effort 2 = 1 dev for 2 weeks, or 2 devs for 1 week).
- Callouts: Reach is a guess (assumption); sellers may lie about damage (open question, same label as in the PRD); build #10 right after launch, re-check Confidence after month 1 (recommendations).

## Critique from another AI → triage
- Sorted it: contradictions (fix now) / bigger issues / opinion.
- #6 was Could and Cut → Won't. "Moves no metric" was weak (the checklist can help close a deal at pickup) → cut for low reach and low impact.
- #9 was a quick win with low value → kept out of the 2×2, like in RICE. Added fill-ins (#2, #6, #7, #10).
- Self-check number was wrong (9 of 10 at 50% before, not 8). Still 8 of 10 now, so it's only a first fix.
- #4 Reach 10 vs Confidence 50%: the AI said they contradict. Not true: the step is required, so Reach 10 is right. The 50% is about sellers **lying** ("No visible damage"), not skipping.
- Defended call switched to #4: ranked first with 50% confidence. Risk: sellers lie. Accepted because Guardrail 1 catches it (photo-match % drops). First said "the damage photo catches it", but the photo is what they'd lie about.
- Not done (optional): 3 confidence levels tied to evidence; same logic for #9 and #10; formatting "Why these numbers".

## End of day (2026-09-24)
- PRD fixed to match the prioritization: #10 → Next, #6 → Cut, MVP "In", "Why", "Out", roadmap and Risk line updated. Repo copy `deliverables/mini-prd.md` updated.
- Didn't just re-upload to Outline, because my mentor made edits there → applied the 9 changes by hand.
- Tomorrow: export from Outline and check it matches; update `problem-frame.md` (old North Star); Day 5 pitch.

---

# Day 5 (Fri 2026-09-25) — Delivery & final video

## Reading
- Used a NotebookLM summary of the readings. Kept 3 ideas for today: Given/When/Then (Then = something you can see), 4 risk responses (avoid, reduce, transfer, accept), story order Why → How → What.
- Why can't a Then check the database? Because QA tests by using the app and only checks what they can see.

## Picking the #1 feature
- Torn between #9 (lets the team count the North Star) and #4 (helps Greg). Picked #4: the task says "top-ranked", and #4 is ranked first in Day 4, so the story stays consistent.
- The #9 measurement spec (another AI's text) isn't Given/When/Then. Kept aside, maybe useful for a hard question in the video.

## Acceptance criteria for #4
- 1st try: "...then he decides to contact the seller" → not testable. That's Greg's decision and the L2 metric, not the feature working. "High quality" also can't be checked.
- 2nd try: "then he presses Message" → still Greg's action (belongs in When).
- Fix: the Then is what the **app** does → "the page shows the photo of the scratches and damage".
- "Shows it" was vague (which of the 6 photos?) → added a "Damage" label.
- Unhappy path ideas: seller skips the step / seller clicks "No visible damage". The second one is a **normal choice**, so it's a second happy path, not an error.
- "Then blocked" → the seller wouldn't know why → "blocked and the damage step is highlighted".
- No-damage text: chose "Seller says: no visible damage" over "No visible damage", because it's the seller's claim, not ReNest's (sellers may lie).

## Top 3 risks
- First list: sellers lie / step annoying / Greg gets scared (2 of 3 from my hints, and all about people). Added my own technical risk: upload fails on a slow phone connection.
- "Greg gets scared by the Damage label" → cut. Not a risk: Greg skips a bad item = the feature working.
- Risk 1 mitigation, 1st try: "incentivize good reviews" → would bias Guardrail 1. Dropped it → accept + monitor: photo-match below 90% → pause and investigate.
- Risk 2: H → M (it's one photo or one click). "Fast and easy" / "look at guardrail" were vague → Guardrail 2, drop of more than 10 points → simplify the step.
- Risk 3: L, because #4 reuses the upload from #1.
- All impacts are H, but likelihood (H / M / L) now tells them apart.

## Go / no-go
- Ship criteria, 1st try: "when they upload a photo or mark no visible damage" → that's what the seller does after launch. Ship criteria are before launch → criteria pass, upload tested on slow connection, guardrail tracking ready.
- Owner: the PM (with input from QA and the dev lead).
- Rollback, 1st try: photo-match below 90% → but turning #4 off doesn't stop lying and gives Greg less truth. Switched to Guardrail 2 (it's the one #4 causes). Mixed up "L2" and "Guardrail 2" for a moment.
- Monitor: L2 moves first (North Star is monthly) → first 2 weeks = L2 + guardrails.
- Recommendation, 1st try: "GO if criteria pass, because guardrails catch risks" → only said it's safe, not why it's worth it. Added the value: shows Greg the real damage before he contacts the seller.

## Video outline (`deliverables/video-outline.md`)
- Problem: first only the first half → added "so good listings go stale and buyers leave" (the "so what?").
- Greg: first only who he is → added his pain ("worries the item won't look like the photos").
- North Star: added how ReNest knows a sale happened (a teammate's question).
- MVP: 5 features → 2 groups (Greg: #1 #4 #8 / Measuring: #2 #9), so it's not a feature list. #10 deferred: "low RICE" was jargon → "only helps the few sellers who forget".
- Risks beat: one risk in detail (lying), two in a few words, plus the rollback trigger.
- Hard question: "Why trust the North Star if the reminder is out?" → used the #9 spec line (listings with only one confirmation) to show how undercounting becomes visible.

## Video + final checks
- Recorded the video with another AI's script, not my outline. Checked it against the task: missing the rollback trigger and "what's next", thin on "why these features" and "why the problem matters" → added 4 clips using lines from my outline.
- Roadmap image from Gemini had made-up features ("Enhanced Seller Messaging", "Buyer Purchase Protection"), wrong names, and only 3 of the 5 MVP features → remade it with the exact PRD names.
- Found that in-app payments is in the video's "Later" but not in the PRD roadmap → add it to the PRD.
- My mentor's tips applied to delivery-plan.md: audience in the intro (designers, devs, QA), a glossary (from memory), 3 callouts (assumption: sellers are honest / open question: few survey answers / recommendation: measure the baseline 4 weeks before launch).
- Baseline defined = the last 4 weeks before launch (the other AI's point was right).
