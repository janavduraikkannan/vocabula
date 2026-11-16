# Vocābula

Latin vocab flashcards for Latin 1 (Vocab Quizzes 1 to 5, door and window sets), part of [Linguae](https://janavduraikkannan.github.io/linguae/).

Live at https://janavduraikkannan.github.io/vocabula/

- **Type, check, rate.** Type the word (a hyphen after a vowel makes a macron: `a-` → `ā`), press Enter, compare, and rate how well you knew it from 1 to 5.
- **Thirteen schedulers**, chosen at the bottom of the home page. Every rating is saved in a per-card review log (time, rating, time taken), and each scheduler works out due times from it, so switching loses nothing.
  - **Default:** FSRS-6 through [ts-fsrs](https://github.com/open-spaced-repetition/ts-fsrs) 5.4.2 (MIT, `vendor/`), exactly as shipped (learning steps 1 and 10 min, relearning 10 min, 90% retention).
  - **Quiz mode:** no formula. Every word in the chosen sets once, in a random order (the session is always that size). At the end: **Try again**, and **Study mistakes** for every word rated below 5. After a Study mistakes round: **Again**, **Study mistakes** (what's still missed) and **Full quiz**. Answers count as reviews for every other scheduler; its mastery is the share of words rated 5 on their latest attempt.
  - **Cram Mode:** each word repeats until rated 5 three times in a row. Finished words return in spaced reviews after the next round, then 2, 4 and 8 rounds later, each until rated 5. Then a test of shuffled groups, finished when a whole group is rated 5 on the first try. Temporary (not remembered); ratings still count as reviews.
  - **Review Mode:** every word once in a random order; a word rated below 5 comes straight back until it gets a 5, and the session ends when every word has been rated 5. No three-in-a-row and no extra review. Temporary (not remembered); ratings still count as reviews.
  - **Legacy:** the first version's card-counting scheduler, written for this site.
  - **SM-2:** Woźniak's 1990 description and SuperMemo 2 plug-in code, including the same-day repeat of anything graded below 4.
  - **Anki SM-2:** rebuilt from Anki's `rslib/src/scheduler/states` with Anki's default deck options and review fuzz (no load balancer).
  - **Ebisu v2:** [ebisu.js](https://github.com/fasiha/ebisu.js) 2.1.3 (public domain, `vendor/`), `defaultModel(24)` hours.
  - **FSRS-7:** ported from [fsrs-rs](https://github.com/open-spaced-repetition/fsrs-rs) `model_v7.rs` with its 34 default weights; checked against haskell-fsrs's reference (states agree to 1e-14).
  - **Leitner:** the 1972 learning box (compartments 1:2:5:8:14, scaled to the selected words).
  - **Leitner (Duolingo)** and **Pimsleur (Duolingo):** the baselines in [duolingo/halflife-regression](https://github.com/duolingo/halflife-regression) (MIT).
  - **Pimsleur:** "A Memory Schedule" (1967): the n-th interval is 5^n seconds.
  - **LSTM** and **GRU:** [srs-benchmark](https://github.com/open-spaced-repetition/srs-benchmark) models with its pretrained weights (`vendor/srs-benchmark-weights.js`); checked against a NumPy version of the same layers.
  - 1–5 buttons map to each source's grades (pass = 3 to 5; Again/Hard/Good/Easy = 1–2/3/4/5; SM-2 quality = 0/2/3/4/5). Predictive models schedule at 90% recall.
- **Mastery** follows whichever scheduler is chosen, in that method's own terms, rebuilt from the review log so switching converts it instantly: predicted recall now for FSRS-6, FSRS-7, Ebisu, both Duolingo models, LSTM and GRU; interval stages for SM-2 (up to 3 weeks); Anki's learning / relearning / young / mature card types; Leitner's five compartments plus learned; progress through Pimsleur's 10 recalls; and the latest 1–5 rating for Legacy. The percent is the average per-word score, unseen words counting as 0.
- **Accounts.** The same account as Verba and the other Linguae sites (`verba-account` in the browser). Progress is saved in `vocab/{account key}` in Firestore project `verba-791ca`, never in the account document. No leaderboard.
- **Firestore security rules** live only in [`firestore.rules` in the linguae repository](https://github.com/janavduraikkannan/linguae/blob/main/firestore.rules). After changing them there, publish them in the Firebase console.

Files: `index.html` (the page), `css/vocabula.css` (styles), `app.js` (screens, saving, account), `engine.js` (word lists, Default and Legacy, queue and saving), `schedulers.js` (the other ten), `vendor/` (ts-fsrs, ebisu.js, srs-benchmark weights); both run in Node for tests. Fēlix art from Verba; icons from game-icons.net (CC BY 3.0).
