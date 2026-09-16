# USCIS 2025 Civics Test — Flashcard Quiz

An interactive flashcard drill for the 128 civics questions on the 2025
USCIS naturalization test (form M-1778). Flip cards, self-grade, take timed
mock tests, and track your progress over time — all in a single HTML file
with no install and no server required.

**Live demo:** open `index.html` in any browser, or visit this repo's
https://qbitprime.github.io/USCIS_2025_Civics_Test_Flashcard_Quiz/

---

## Using the tool

### Practice mode (default)
- Tap a card to flip it and reveal the accepted answers.
- Grade yourself: **✗ Missed it** or **✓ Got it right**.
- Get a question right **3 times in a row** and it's retired from the deck
  ("mastered") — it won't show up again until you reset it.
- Already know a question cold? Click **"✓ I already know this — mark
  mastered"** to skip the streak and retire it immediately.
- Each session shuffles the deck and shows every question once before
  repeating — no more seeing the same card back-to-back.
- The **★ 65/20** filter switches to just the 20 starred questions, for
  applicants 65+ with 20 years of permanent residency.

### Mock Test mode
Switch to **Mock Test** at the top for a timed, realistic run:
- **All 128** filter → 20 random questions, need 12 correct to pass.
- **★ 65/20** filter → 10 random questions, need 6 correct to pass.
- The test ends the moment passing or failing is mathematically decided,
  just like the real interview — it won't always run the full 20 (or 10)
  questions.

### Tracking your progress
- Every card shows an **all-time right/wrong count** under the question.
- Click **🎯 Focus areas** to see your most-missed and strongest questions
  at a glance, so you know where to spend your remaining study time.
- Progress (mastered cards, streaks, right/wrong history) saves
  automatically. If your browser session doesn't support that, use the
  **🔗 Auto-sync to a local file** or **⭳ Backup / ⭱ Restore** buttons to
  keep a copy on disk.

### Dark mode
Click the 🌙 icon top-right to switch themes for low-light studying. Your
choice is remembered.

---

## ⚠️ Before you rely on this for your interview

Four questions have **personalized answers already filled in** for one
specific address. **You must update them to match your own state,
district, and current officials** — using someone else's answers at your
actual USCIS interview will get those questions marked wrong.

| # | Question | What to check |
|---|----------|----------------|
| 23 | Name one of your state's U.S. senators | [senate.gov/states](https://www.senate.gov/states/) |
| 29 | Name your U.S. representative | [house.gov/representatives/find](https://www.house.gov/representatives/find-your-representative) |
| 61 | Who is the governor of your state | Search "[your state] governor" |
| 62 | What is the capital of your state | General knowledge / search |

Four more questions ask for the **current national officeholders**
(President, Vice President, Speaker of the House, Chief Justice). These
are already filled in but can change — double-check them against
[uscis.gov/citizenship/testupdates](https://www.uscis.gov/citizenship/testupdates)
close to your interview date, since USCIS requires the name of whoever is
serving at the time of your interview.

### How to edit the answers

1. Open `index.html` in a text editor (VS Code, Notepad++, or even a
   plain text editor).
2. Search for `const QUESTIONS = [` — this is the master list of all 128
   questions.
3. Find the question by its number, e.g. for question 23:

   ```js
   {id:23,cat:'system',star:false,q:`Who is one of your state's U.S. senators now?`,a:[`Rick Scott`,`Ashley Moody`],note:`Filled in for Gulfport, FL 33707. Good through your Sept 18, 2026 interview — Florida's Senate election isn't until Nov 3, 2026.`,imgQuery:[`Rick Scott`,`Ashley Moody`]},
   ```

4. Replace the names inside the **`a:[ ... ]`** part with your own state's
   answers. Each name goes in backticks (`` ` ``) separated by commas:

   ```js
   a:[`Senator One Name`,`Senator Two Name`]
   ```

5. Optional — update or delete the **`note:`** text (it's just a reminder
   shown on the card; it doesn't affect grading).
6. Optional — update **`imgQuery:`** with the new name(s) so the photo on
   the back of the card matches. It pulls a thumbnail live from Wikipedia,
   so use whatever the person's Wikipedia article is titled. You can also
   delete the whole `imgQuery:` field if you'd rather not show a photo.
7. Repeat for questions **29**, **61**, and **62**.
8. Save the file, then re-upload it to this repo (or re-run
   `git add / commit / push` if you're using the command line) to update
   the live GitHub Pages version.

**Tip:** every field is comma-separated and wrapped in matching backticks
or square brackets — if the page stops working after an edit, it's almost
always a missing comma, bracket, or backtick near where you edited. Undo
your last change and try again more carefully.

---

## Disclaimer

This is an independent study aid, not an official USCIS product. Question
text and accepted answers are taken from the official USCIS M-1778 (2025
version) study guide, but USCIS notes that additional correct answers may
exist beyond what's listed. Always confirm time-sensitive answers (current
officeholders) at
[uscis.gov/citizenship/testupdates](https://www.uscis.gov/citizenship/testupdates)
before your interview.
