# USCIS 2025 Civics Test — Flashcard Quiz

An interactive flashcard drill for the 128 civics questions on the 2025
USCIS naturalization test (form M-1778). Flip cards, self-grade, take timed
mock tests, and track your progress over time — all in a single HTML file
with no install and no server required.

**Live demo:** open `index.html` in any browser, or visit this repo's
[GitHub Pages link](../../settings/pages) once it's enabled.

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

### Dark mode
Click the 🌙 icon top-right to switch themes for low-light studying. Your
choice is remembered the same way your progress is (see below).

---

## Where does your progress get saved?

Short version: **automatically, in your own browser, on your own device —
nothing is sent to me, to GitHub, or to anyone else.** No account, no
login, no server involved.

Here's exactly what happens, in order:

1. **Normal case (this website):** progress is saved using your browser's
   built-in `localStorage`, scoped to this exact page. It persists across
   closing the tab, closing the browser, and restarting your computer.
   It does **not** follow you to a different browser or a different
   device — `localStorage` is tied to one browser on one machine.
2. **If your browser blocks that** (some privacy modes, very locked-down
   settings, etc.), the tool falls back to the optional local-file/backup
   options below, and the status line under the toggles will tell you
   plainly that automatic saving isn't available.
3. *(If you're running this inside Claude.ai's own preview instead of the
   live website, it also checks for an account-level storage API first —
   not relevant for anyone using the actual GitHub Pages link.)*

### About the JSON file / "Auto-sync" and "Backup" buttons

These are **entirely optional** — the quiz saves your progress
automatically without you touching them. They exist for two situations:
you want a real file on disk as a backup, or you want to move your
progress between two different browsers/devices (since `localStorage`
alone can't do that).

- **🔗 Auto-sync to a local file** — click once, pick (or create) a
  `.json` file on your computer, and from then on every answer you grade
  writes to that file automatically in the background, no further clicks.
  Chrome/Edge only (this uses the File System Access API, which Safari
  and Firefox don't support yet).
- **⭳ Backup to file** — downloads a one-time snapshot of your progress
  as a `.json` file, right now, wherever your browser saves downloads.
- **⭱ Restore backup** — loads a previously saved `.json` file back into
  the app. Useful if you cleared your browser data, switched computers,
  or want to pick up where you left off somewhere else.

None of this ever touches a server — the file only ever exists on your
own computer, and only if you explicitly created one.

---

## ⚠️ Before you rely on this for your interview

Four questions ship with a generic **"Answers will vary"** placeholder,
because the correct answer depends on where you live. **You must fill
these in with your own state's information** — the real interview needs
your actual senators, representative, governor, and capital, not anyone
else's.

| # | Question | Where to look it up |
|---|----------|----------------------|
| 23 | Name one of your state's U.S. senators | [senate.gov/states](https://www.senate.gov/states/) |
| 29 | Name your U.S. representative | [house.gov/representatives/find](https://www.house.gov/representatives/find-your-representative) |
| 61 | Who is the governor of your state | Search "[your state] governor" |
| 62 | What is the capital of your state | General knowledge / search |

Four more questions ask for the **current national officeholders**
(President, Vice President, Speaker of the House, Chief Justice). These
come pre-filled with whoever held the role as of this file's last update,
but that can change — double-check them against
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
   {id:23,cat:'system',star:false,q:`Who is one of your state's U.S. senators now?`,a:[`Answers will vary.`],note:`Personal to you — look up your own state's senators before test day. (D.C. and territory residents: your answer is that you have no U.S. senators.)`},
   ```

4. Replace the placeholder inside the **`a:[ ... ]`** part with your own
   state's answers. Each name goes in backticks (`` ` ``) separated by
   commas:

   ```js
   a:[`Senator One Name`,`Senator Two Name`]
   ```

5. Optional — update or delete the **`note:`** text (it's just a reminder
   shown on the card; it doesn't affect grading).
6. Optional — add an **`imgQuery:`** field with the person's name so a
   photo shows up on the back of the card. It pulls a thumbnail live from
   Wikipedia, so use whatever that person's Wikipedia article is titled,
   e.g. `imgQuery:\`Jane Q. Senator\`` (or `imgQuery:[\`Name One\`,\`Name
   Two\`]` for the two-senator question). Leave it out if you'd rather not
   show a photo.
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
