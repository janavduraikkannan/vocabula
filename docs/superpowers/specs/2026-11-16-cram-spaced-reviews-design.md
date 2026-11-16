# Cram Mode: spaced reviews

## Why
Cram Mode works but takes too long. With no misses, a 15-word set took 165 cards, and 105 of them (64%) were
reviews. After every round, every earlier word came back. Those reviews felt like repeats of cards just seen.

## Goals / non-goals
- Goal: cut the time to finish a set without making it less effective.
- Rounds stay unchanged: three 5s in a row per word.
- The test stays unchanged: shuffled groups that repeat until one is all 5s on the first try.
- Non-goal: changing the 1–5 rating buttons. A Wrong/Correct version was considered and dropped, because the
  mastery donuts and the other schedulers rely on 1–5 ratings.

## Approaches considered
1. **Spaced reviews (chosen).** A finished word comes back after the next round, then 2 rounds later, then 4, then 8,
   and then not until the test. It keeps reaching older words before the test does, and the growing gaps make
   recall stick better.
2. Recent words only: review the last 3 finished words. Older words go unseen until the test, and a forgotten one
   there restarts the whole group of 15.
3. No reviews. Fastest, but the test becomes the only check, so the time saved tends to return as extra test groups.

## Design
- `CRAM_GAPS = [1,2,4,8]` in `engine.js`. Each gap counts from the word's previous review.
- Each review card still repeats until it gets a 5.
- A 5 on the first try moves the word to its next gap. Anything lower puts it back to coming after the next round.
- After each round, only the words due then are reviewed, in a random order. If none are due, the next round starts.

## Result (Node simulation, 15 words)
| | Before | After |
|---|---|---|
| No misses | 165 cards (105 reviews) | 94 cards (34 reviews) |
| 10% of ratings below 5, average | 252 cards | 175 cards |
