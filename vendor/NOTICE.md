# Third-party files in this folder

| File | What it is | License |
|---|---|---|
| `ts-fsrs-5.4.2.umd.js` | ts-fsrs 5.4.2, unmodified | MIT (`ts-fsrs-LICENSE.txt`) |
| `ebisu-2.1.3.min.js` | ebisu.js 2.1.3 | Public domain / Unlicense (`ebisu-UNLICENSE.txt`) |
| `srs-benchmark-weights.js` | Pretrained GRU and LSTM weights extracted from the `pretrain/` folder of [open-spaced-repetition/srs-benchmark](https://github.com/open-spaced-repetition/srs-benchmark) | **License unclear.** That repository has no license file that I could find, so these weights are **not covered by this repository's AGPL-3.0 grant** and no license is claimed for them. They are included only until the upstream license is clarified. |

Code in `../schedulers.js` that was ported from other projects keeps their licenses:

- **FSRS-7** from [fsrs-rs](https://github.com/open-spaced-repetition/fsrs-rs): BSD 3-Clause, copyright 2023 Open Spaced Repetition (`fsrs-rs-LICENSE.txt`).
- **Anki SM-2** from [Anki](https://github.com/ankitects/anki): AGPL-3.0-or-later.
- **Duolingo's Leitner and Pimsleur baselines** from [duolingo/halflife-regression](https://github.com/duolingo/halflife-regression) (`experiment.py`): MIT, copyright 2016 Duolingo Inc. (`halflife-regression-LICENSE.txt`). The MIT license is stated in that repository's `LICENSE.md`, its README and the header of `experiment.py`.
- **SM-2** follows Piotr Woźniak's 1990 article "Application of a computer to improve the results obtained in working with the SuperMemo method" and his SuperMemo 2 plug-in source code. The SM-2 algorithm is copyright SuperMemo World (supermemo.com), which has said it permits use of SM-2 in other software provided its copyright note is kept. Credit: SM-2 algorithm by Piotr Woźniak, SuperMemo World.
