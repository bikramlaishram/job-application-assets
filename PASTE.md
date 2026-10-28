# Ajaia Product Manager Assessment — SidelineReel
**Candidate:** Bikram Laishram  
**Email:** high.sailor@gmail.com  
**Video:** https://raw.githubusercontent.com/bikramlaishram/job-application-assets/main/docs/video/ajaia_Ajaia_SidelineReel_PM_walkthrough.mp4  
**Working prototype:** https://bikramlaishram.github.io/job-application-assets/sidelinereel/  
**Resume:** https://raw.githubusercontent.com/bikramlaishram/job-application-assets/main/Bikram_Laishram_AI_Native_PM_CV.pdf  
**Shipped work:** https://github.com/bikramlaishram · https://github.com/acuitygen · LinkedIn https://www.linkedin.com/in/bikramlaishram  
**Product reference:** https://ajaia.ai  

---

## Task 1. The roadmap call

### What SidelineReel builds next (ranked)

| Rank | Candidate | Verdict | Evidence |
|---|---|---|---|
| **1** | **Roster tagging accuracy (jersey → kid)** | **Build now** | Three support tickets this week across Ridgeline, Brightwater, Cobblestone: #14↔#4, swapped digits, #1↔#11. Analytics note: ~30% of reels never open; wrong-kid thumbnails are a named cause. One ticket is from Ridgeline ($180k) itself — quality risk on the renewal account without shipping livestream. |
| 2 | Notification timing / open-rate for generated reels | Next after tagging | Same health note: late-night notifications also drive unopened reels. Fixes the denominator behind the 92% “share rate” vanity. |
| 3 | Coach “ambiguous tag” review queue (human-in-loop for low confidence) | Part of #1 ship | Needed so production OCR/vision mistakes don’t silently publish. |
| 4 | More Reel Editor / trim + music controls | **Not next** | Survey: 58% of 210 named editing as top ask. Usage: 6% opened editor; **&lt;1% of openers finished an edit**. Stated preference ≠ revealed preference. |
| 5 | Full livestreaming for Ridgeline | **Not next** | Loudest ask (Carla + Sales, $180k, 6 weeks). Outside the core job (highlights + weekly auto-recap). Huge lift; no usage/survey evidence it is the retention driver. Carla already said highlight reels drove half of parent renewals. |

### What I would NOT build next (and why)

**I would not commit to full livestreaming before Ridgeline signups.** It fails the “evidence vs who is asking” test. The board wants live; parents renewed for highlights. Shipping livestream under renewal panic risks a multi-month distraction while wrong-kid reels continue to burn trust — including at Ridgeline.

**I would not expand Reel Editor controls next** despite the survey win. Behavior says almost nobody completes an edit; auto-recap share is used in **90%** of recaps. Double down on the automatic loop, not the manual one.

### Concrete answer to Carla / Sales (without livestream)

Within 6 weeks we commit to: (1) ship roster-tag disambiguation + human review for low-confidence jersey matches; (2) measure wrong-kid rate and unopened-reel rate weekly; (3) give Ridgeline a named weekly quality readout. That is a concrete yes on *their* filed defect class, not a fake livestream promise.

### Decision rule used

Read every material. Weight multi-club defect + analytics explanation over single-account roadmap pressure. Protect the core job: right kid on the reel, auto-recap families actually open and share.

---

## Task 2. The spec — Roster Tagging Accuracy (jersey disambiguation)

### Outcome
Reduce wrong-kid clips in personal reels and wrong-kid thumbnails that suppress opens. Target (90 days post-ship): **≥50% reduction** in support tickets tagged “wrong player / wrong jersey,” and **≥20% relative reduction** in never-opened reels attributed to thumbnail mismatch (analytics + support taxonomy).

### In scope
- Vision/OCR jersey read with **confidence score**.
- Lookalike digit rules (1/11, 4/14, swapped digits).
- **Coach review queue** for confidence below threshold or lookalike set size &gt; 1.
- On confirm: reassign clip to correct roster player; regenerate personal reel + weekly recap thumbnail; remove clip from wrong kid.
- Audit log (who confirmed, before/after player ids).
- Club-level wrong-tag rate dashboard for Success/Sales (Ridgeline pack).

### Out of scope
- Livestreaming / real-time broadcast.
- Parent Reel Editor expansion (trim, music, overlays).
- App icon / watermark bugs (log separately; not this epic).
- Rebuilding camera hardware pipeline.
- Fully automatic publish with no human path when confidence is low.

### Where a human stays in the loop
- Coach (or club admin) confirms identity when confidence &lt; threshold or multiple roster candidates remain.
- Support can force re-tag from a ticket.
- PM/eng review weekly wrong-tag rate; threshold tuning is a human decision.

### Acceptance criteria (testable)
1. Given a clip whose top-2 jersey hypotheses are {4, 14} with confidence &lt; 0.7, the clip **does not** auto-publish to a personal reel; it appears in the review queue within 2 minutes of processing.
2. After coach selects #14 Ava Reyes, Ava’s reel contains the clip and Noah (#4) does not; recap thumbnail for that moment shows #14.
3. Lookalike pairs {1,11}, {4,14}, digit-swap pairs are covered by unit tests / evaluation set of ≥50 labeled clips.
4. Support ticket template includes “wrong player” reason code; weekly report counts them by club.
5. If coach chooses “Hold out of reels,” clip is absent from all personal reels and the weekly auto-recap.

### Top two failure modes + detection
1. **Queue fatigue → coaches rubber-stamp.** Detection: time-to-confirm &lt; 2s at high volume; disagreement rate vs later parent tickets; A/B require replay of 1s of clip before confirm enabled.
2. **Threshold too low → still auto-publishes wrong kids.** Detection: wrong-tag ticket rate not falling after 2 weeks; shadow-mode disagreement between auto-tag and coach on held-out games; page if wrong-tag rate &gt; baseline.

---

## Task 3. Working prototype

**Link:** https://bikramlaishram.github.io/job-application-assets/sidelinereel/

**Core flow (2–3 steps):**
1. Review queue of ambiguous jersey matches (confidence + lookalike reason).
2. Select correct roster player (or hold clip out).
3. Confirm → corrected personal reel preview.

Built as a runnable HTML app (no login). Reference to https://ajaia.ai is in the footer.

---

## Task 4. AI Workflow Note

- **Used AI for:** structuring the roadmap table against the five materials; drafting the spec skeleton; generating the interactive HTML prototype; drafting this Markdown; assisting narration/script for the video.
- **Kept human:** the priority call (tagging over livestream and over survey-led editor), the explicit “no” to Carla’s livestream ask, acceptance criteria and failure modes, and the salary / why-Ajaia close.
- **Checked / rejected:** an early AI suggestion to prototype the personal-reel *viewer* and weekly recap sender as the “core flow.” That describes today’s product, not the top roadmap item. I rebuilt the prototype around **roster tag review** so Task 3 matches Task 1–2.

---

## Video walkthrough notes (companion to the recording)

I am **Bikram Laishram**, Senior Product Manager at MariApps Marine Solutions; previously founded OceanAI (~20 people) and shipped LLM products to ~80 enterprise customers. I build AI-native products and still ship with coding agents (GitHub: bikramlaishram / acuitygen).

**Why this role / why Ajaia:** Ajaia’s assessment itself is the product culture I want — AI as co-pilot, evidence over loud stakeholders, PMs who can ship a working slice. SidelineReel’s job-to-be-done (right kid, family recap) is a crisp outcome loop.

**Salary expectations for this role:** ₹50–60 LPA total cash for an India-remote Senior/Staff PM seat (flexible for equity / leveling). Current compensation not disclosed per instructions.
