# CLAUDE.md — a module of the Interactive Pathology Teaching Platform

This repository is one module (a single `index.html`): **Neoplasia (New)** (module key `neonew`, storage prefix `nn_`,
build `new-1.1`). Built 2026-10-30 from the user's own syllabus "Neoplasia (Ch. 6)", pp. 42–64, **as it is — NOT condensed**
(an exception to HANDBOOK §4.2, like Inflammation (New)), with the app code of `third-year-med/neoplasia`. It is separate from
the Neoplasia module (`neoplasm`, `nm_`) — never mix their keys, storages or IDs.

The platform's decisions, the checklist for modules, the deployment steps, the testing workflow and the lessons learned are
in the platform repository: `third-year-med/Interactive-pathology-platform` → `CLAUDE.md` and `docs/HANDBOOK.md`
(rebuilds: `docs/REBUILD.md`).

- The course data in `index.html` is encrypted with this module's OWN content key, which lives only in the user's Code.gs
  (`CONTENT_KEYS.neonew`). Never commit a key or an unencrypted copy of the course.
- The `<script id="platform-nav">` block is maintained in the platform repo (`modules/platform-nav.js`) and written here
  with `tools/module-release.js refresh` — do not edit it by hand.
- Stable IDs: topics t01–t14 in the syllabus order + **t15 Practical Pathology** (build new-1.1, 2026-10-31: the Practical topic
  of `neoplasm` copied — s1501–s1509 — plus picture sections s1510–s1512), sections sNNMM, questions q001–q161 (q001–q096 reused
  from `neoplasm`, each with `from: 'neoplasm:qNNN'`; q097–q155 the syllabus MCQs/EMQ and new questions; q156–q161 the practical
  topic's own questions from `neoplasm`), cases c01–c08. Atlas pictures keep their `nm-img-NNN` ids (the same pictures as in Neoplasia).
  The 7 syllabus figures are embedded (SVG-wrapped JPEG, credit "Course syllabus — Neoplasia (Ch. 6), p. N").
- Delivered to the user directly, never committed: the Robbins picture-import file (`neonew-pictures-robbins.json`,
  keys `nn-robbins-01…39`, chosen from `nm-robbins6-*` and `nm-robbins-pbd-*`) and the 🔒 assessment-only bank
  (`neonew-assessment-bank.json`, items `aqb_nn_NNN[letter]` from the user's "MCQ neoplasia Dr Helal", Q388–454, with the
  book's answer key) — both imported by the user in ✏️ Edit master draft.
- Practical package (new-1.1, never committed): `neonew-practical-pictures.json` (24 Robbins / syllabus pictures `nn-prac-01…24` →
  t15 sections), `neonew-practical-cases.json` (15 practicals `nn-pr-01…15`), `neonew-spotter-questions.json` (52, 2 per picture on
  26 pictures incl. atlas nm-img-089/091; answers A–E 11/11/10/10/10) and `neonew-ospe-stations.json` (18 × 4 parts). PEIR
  pictures are NOT used in Spotter/OSPE: peir.path.uab.edu is outside the session's network policy, so they cannot be examined.
- Test changes on the real page with the platform repo's e2e test "Neoplasia (New) module (neonew)" (`NN_CONTENT_KEY` in the
  environment) and `node test/module-smoke/smoke.js` before pushing.
