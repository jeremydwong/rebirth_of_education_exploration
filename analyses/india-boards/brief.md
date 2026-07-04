# India Boards Project — Brief for Claude Code

*Portfolio analysis living inside a shared education-data repo. Owner: Petrichor. This file is the source of truth for scope; paste it into the repo at `analyses/petrichor-india-boards/BRIEF.md`.*

---

## 1. The question (one piece, three organs)

**Anchor question:** Does India's "better" syllabus (CBSE/ICSE vs. state boards) actually *teach* better, or does it *select* better students — analogous to Alberta charter schools / Ontario Catholic schools, where observed gaps are largely composition?

**Method organ (from Q3):** Within-village / within-area comparisons as the identification strategy. ASER samples households in villages, so children from the same village attending different school types are directly comparable — neighborhood effects are killed by construction. Benchmark against Muralidharan & Sundararaman's Andhra Pradesh school-choice RCT (two-stage voucher lottery): does the descriptive data replicate the RCT's finding that most of the private-school advantage is selection?

**Discussion organ (from Q2):** The pedagogy paradox sidebar (~300 words in the write-up): Indian classrooms are drill-heavy, and drill-based Direct Instruction is among the best-evidenced methods ever tested (Project Follow Through) — so why doesn't Indian rote produce DI's results? Rote is DI minus the load-bearing parts (sequencing, mastery checks, immediate correction). Bridge: Beatty & Pritchett "Slow Down, You're Going Too Fast" (overambitious curricula) → Teaching at the Right Level (Pratham/J-PAL) as the India-tested cousin.

**Framework:** Pritchett's systems lens is the *narrative*, not a regression variable. Six principles (open entry/exit, locally operated, performance pressured, professionally networked, technically supported, flexibly financed) = governance axis. Beatty–Pritchett curriculum-pacing critique = curriculum axis. Key reading: Pritchett, "Risks to Education Systems from Design Mismatch and Global Isomorphism" (UNU-WIDER 2014).

## 2. Known landmines (write these into the analysis, don't hide them)

1. **Board exams are not comparable across boards** (each board sets/grades its own exam). Never use board results as the outcome measure.
2. **Board and management are confounded:** ICSE ≈ all private; state board skews government; CBSE mixed. Curriculum-only contrasts require off-diagonal cells (e.g., private-unaided CBSE vs. private-unaided state board).
3. **KV vs. neighboring state-govt school is NOT a clean curriculum contrast** — Kendriya Vidyalayas are better funded and staffed. Curriculum + resources, not curriculum alone.
4. **The board+outcome linkage may not exist:** ASER records govt/private but not board; U-DISE+ records board but has no outcomes; NAS has outcomes and some board coverage but documented reliability problems (state averages inflated; rankings uncorrelated with ASER/IHDS). If board+outcome can't be credibly linked → fall back to the management version of the question (still a strong piece).
5. **No score harmonization.** Do not combine ASER/NAS/IHDS onto one scale. Triangulate instead: run the same comparison within each dataset and ask if the pattern replicates.
6. **PISA cannot carry an India question:** India skipped 2022, only real participation was 2009 (TN + HP, unrepresentative), planned samples were cream-skimmed (Chandigarh, KVs, Navodayas). PISA data in the shared repo is context/benchmark only.

## 3. Phase 0 — data audit (do this before any analysis)

Deliverable: `data-audit.md` — a table of {dataset × variables × granularity × access × does it link outcome↔board?}.

- [ ] **ASER** (asercentre.org): confirm downloadable microdata vintage; variables: village ID, school type (govt/pvt), reading/arith levels, child age/grade. Board recorded? (expected: no)
- [ ] **U-DISE+** (udiseplus.gov.in): school-level board affiliation + management + resources. Outcomes? (expected: no). Geographic granularity for within-area joins (district/block/village code).
- [ ] **IHDS-II**: school-type detail (govt / aided / private / convent), short learning assessment, rich SES. Check school questionnaire for board/medium. Vintage caveat (2011–12).
- [ ] **NAS 2021**: board and management coverage; use only with the reliability caveat stated inline.
- [ ] **Young Lives (India / AP cohort)**: school survey rounds — board info + test scores? Access terms?
- [ ] Decision gate: which comparison is actually identifiable — (a) curriculum within management, (b) management within village, (c) both?

## 4. Repo carve-out (attributable slice, collaborative repo)

```
analyses/
  petrichor-india-boards/
    BRIEF.md          ← this file
    README.md         ← question statement in my voice + findings summary (job-hunt landing page)
    data-audit.md
    data/
      raw/            ← gitignored if large; document sources + download scripts instead
      processed/
    sql/              ← the SQLite data model + analysis queries (numbered: 01_load, 02_clean, ...)
    notebooks/        ← pandas cleaning + any stats
    dashboard/        ← Tableau workbook or link to Tableau Public
    writeup/          ← the 800–1,200 word analysis
```

Working norms (collaborative project — no fence, just legibility):
- This is an openly collaborative analysis; contributions from collaborators are welcome anywhere in it, including this directory.
- Commit under my own name / normal git identity — git history is the only attribution mechanism needed.
- README.md top line: one-paragraph question statement, framed as "a collaborative project; my role: identification strategy, SQL data model, dashboard, write-up" (adjust to actual division of labor) + link to Tableau Public + link to write-up. A hiring manager should get the whole story from that one file.
- The write-up and dashboard are in my voice regardless of who touched the pipeline.
- Skill-building constraint (the one real rule): the SQL and Tableau under my name must be work I can reproduce from scratch — the point of this project is building those muscles for interviews, so collaborate on everything, but don't outsource the parts I'm here to learn.
- Shared-repo courtesy: add one line to the repo root README pointing at this analysis; don't restructure anyone else's directories without discussing.

## 5. Build phases (maps to upskilling plan weeks 4–5)

**Phase 1 — data model (SQL showcase):** download → load into SQLite (DB Browser or `sqlite3` CLI) → cleaning queries → analysis tables. Every join and window function here is portfolio evidence; keep the SQL readable and commented.

**Phase 2 — analysis:** (a) raw gaps by school type / board where available; (b) within-village (ASER) or SES-conditioned (IHDS) gaps; (c) the shrinkage from raw → adjusted IS the finding. Effect sizes, not just point estimates.

**Phase 3 — dashboard (Tableau Public):** 3–5 views max. Suggested: raw gap vs. adjusted gap side-by-side; state-level map; the off-diagonal comparison if identifiable.

**Phase 4 — write-up:** question → data → method → findings → *what this can't conclude* (the landmines section, worn proudly) → pedagogy-paradox sidebar → Pritchett systems narrative as the close. Publish; 3-sentence LinkedIn version.

## 6. Reading list (skim for vocabulary, cite in write-up)

- Muralidharan & Sundararaman, "The Aggregate Effect of School Choice" (AP voucher RCT) — the benchmark
- Beatty & Pritchett, "Slow Down, You're Going Too Fast" (2015)
- Pritchett, "Design Mismatch and Global Isomorphism… Examples from India" (UNU-WIDER 2014)
- Johnson & Parrado, "Assessing the Assessments" (ASER vs NAS reliability) — the caveats section
- Banerjee et al., balsakhi / TaRL evaluations (J-PAL)
- Stockard et al. 2018 DI meta-analysis + a Project Follow Through summary — for the sidebar
- ASER national report (latest) — for metric definitions and vocabulary
