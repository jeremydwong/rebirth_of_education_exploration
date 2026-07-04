# Data Audit — India Boards Project (Phase 0)

*Deliverable per [BRIEF.md](brief.md) §3. Question being audited: for each candidate dataset, can it link a **learning outcome** to a **school board** (CBSE / ICSE / state), and at what granularity? Audit date: July 2026.*

**Bottom line first:** the board↔outcome linkage the anchor question wants **does not exist in any public unit-level dataset** (landmine #4 confirmed). The identifiable comparison is **management (govt vs. private) within village/SES**, triangulated across ASER, IHDS-II, and Young Lives — with U-DISE+ used descriptively to quantify the board×management confound and locate the off-diagonal cells. See the decision gate at the end.

---

## 1. Summary table

| Dataset | Vintage | Outcome measure | School type / management | Board recorded? | Geographic granularity | Access | **Links outcome↔board?** |
|---|---|---|---|---|---|---|---|
| **ASER** | Annual 2005–14; alternate yrs 2016, 2018, 2022, 2024 | ✅ Child-level reading (letter→story) & arithmetic (digit→division), ages 5–16 | ✅ Govt / private / other (+ tuition) | ❌ No (expected, confirmed: not in survey framework) | Village (30/district, 20 HH/village) — village ID in microdata | Microdata **by email request** (contact@asercentre.org); district aggregates downloadable | ❌ **No** — but ✅ outcome↔management *within village* |
| **U-DISE+** | Annual census; microdata portal from 2018-19 | ❌ None | ✅ 17 management categories | ✅ Yes — affiliation board on school report cards (secondary/hr-sec) | School (11-digit UDISE code) → state/district/block/village-location codes; ~1.5M schools | Data Sharing Portal (microdata.udiseplus.gov.in), OTP registration; per-school report cards public | ❌ **No** — board without outcomes. Role: quantify the board×management confound |
| **IHDS-II** | 2011–12 (vintage caveat) | ✅ Short reading/writing/arithmetic tests, children 8–11 (Pratham-designed) | ✅ Detailed: govt / govt-aided / private / convent / madrassa; EGS; fees; medium | ❌ No in household module; primary-school questionnaire covers 1 govt + 1 pvt *primary* school (board largely N/A below secondary) | Village / urban block PSU; 42,152 HH, 1,503 villages + 971 urban blocks | ✅ **Fully public now** — ICPSR/DSDR study 36151, free registration, Stata/SPSS/R | ❌ **No** — but ✅ outcome↔management with rich SES controls |
| **NAS 2021** | Nov 2021 | ✅ Classes 3/5/8/10, language/math/science | ✅ Govt / govt-aided / private-unaided (published breakdowns) | ◐ Class 10 frame spans state boards + CBSE, but published disaggregation is by *management*, not board | District report cards (720 districts, 118k schools, 3.4M students) — **aggregates only** | Report cards & PARAKH dashboard public; **no unit-level microdata** ("does not provide scores for individual students or schools") | ◐ **Aggregate-only, unreliable** — Johnson & Parrado: state averages inflated, rankings uncorrelated with ASER/IHDS. Caveated triangulation at most |
| **Young Lives (India school survey)** | 2010-11 (primary); **2016-17 (Class 9, AP+Telangana)** | ✅ Linked start/end-of-year tests: maths, functional English, transferable skills → **value-added** | ✅ Sample stratified across state-govt / private-aided / private-unaided / tribal-welfare schools | ◐ Plausibly recoverable from school questionnaire — **verify in UKDS docs** (see §2.5) | Pupil–class–school hierarchy; ~9,000 pupils, ~205 schools; AP+TS only | ✅ UK Data Service, free registration, standard EUL. 2010-11 = SN 7478 (also on World Bank microdata); 2016-17 in same series (Vietnam counterpart = SN 8360) | ◐ **Closest thing to yes**, small-N, 2 states — and the only dataset with score *growth* |
| **Young Lives (household panel)** | Rounds 1–7, 2002–2024 (cohorts born ~1994 & ~2001) | ✅ Repeated cognitive tests (PPVT, maths, reading) at ages ~5/8/12/15/19/22 | ✅ School type each round + education expenditure incl. fees | ❌ No | Child-level panel, ~3,000 children, AP+TS sentinel sites | ✅ UK Data Service, free registration (R1–R5 public; R6–7 rolling) | ❌ No board — but the **only data tracing the same child through enrolment, fees, dropout (with reasons), and later scores** (see §6) |
| **NSS 75th rd., Sch. 25.2 (Education)** | Jul 2017–Jun 2018 | ❌ Attainment/enrolment only, no test scores | ✅ Govt / pvt-aided / pvt-unaided | ❌ No | Individual within household; national, ~113k HH; district identifiable | ✅ **Fully public** — [microdata.gov.in catalog 151](https://microdata.gov.in/NADA/index.php/catalog/151), free registration | ❌ No — role: **fees actually paid, waivers/free-ships, and coded dropout reasons** at national scale (see §5–6) |

### Already in this repo (don't reinvent)

| File | What it is | Use here |
|---|---|---|
| [pisa-data-academic-performance.csv](../../pisa-data-academic-performance.csv) | OWID extract: PISA math means, country×year (453 rows, 2000–2022) | Context/benchmark only, per landmine #6 (India = TN+HP 2009 only) |
| [intro-report.md](../../intro-report.md) | PISA cross-country report (Pritchett framing, §4 model, India ≈345 context) | Source for framing + the β₂/β₃ narrative; India board exams discussion in §7 |
| [caplan_data_case/](../../caplan_data_case/) | Bryan Caplan's *Case Against Education* return-to-education workbooks (authored `bcaplan`, 2014–15; US data by student quality × gender × major) | Thematic companion for the **selection vs. treatment** argument; no India linkage |

None of the in-repo data touches board↔outcome, so the audit below drives the design.

---

## 2. Dataset notes

### 2.1 ASER — the within-village engine ✅ (primary dataset)

- **What it is:** household-based rural survey; all children 3–16 in sampled households get schooling status; 5–16 tested on basic reading (letter / word / paragraph / story) and arithmetic (number recognition / subtraction / division). Because sampling is by *household within village*, children from the same village attending govt vs. private schools are directly comparable — neighborhood effects killed by construction (the Q3 method organ).
- **Vintages:** annual 2005–2014; alternate-year "basic" model from 2016 → 2016, 2018, 2022, 2024 are the full rural rounds (2020–21 were phone surveys — avoid). Target vintage: **2018 and/or 2022/2024** depending on what the Centre releases.
- **Board:** not recorded — only govt/pvt/other + whether the child takes paid tuition. Confirmed by the [ASER assessment framework](https://img.asercentre.org/docs/Bottom%20Panel/Key%20Docs/aserassessmentframeworkdocument.pdf) and [FAQ](https://img.asercentre.org/docs/ASER%202022%20report%20pdfs/All%20India%20documents/FAQ/frequentlyaskedquestionsaboutaser.pdf).
- **Access friction (the schedule risk):** unit-level data is **by email request** to contact@asercentre.org; district-level aggregates are downloadable from [asercentre.org](https://asercentre.org/aser-survey/). → **Send the request email first, before anything else in Phase 1.**
- **Caveats:** rural only; SES controls are thin (household assets in some rounds); tuition variable matters (private-school kids also buy more tutoring — bundle, not curriculum).

### 2.2 U-DISE+ — board×management structure, no outcomes

- **What it is:** the administrative census of ~1.5M schools ([udiseplus.gov.in](https://udiseplus.gov.in/)). School report cards record **affiliation board** (CBSE/ICSE/State) for secondary and higher-secondary schools, plus management (17 categories), teachers, infrastructure, enrolment.
- **Access:** bulk school-level microdata via the [Data Sharing Portal](https://microdata.udiseplus.gov.in/) — OTP registration + a 250-character purpose statement; raw data has been shared from 2018-19 onward. Individual school report cards are public without registration.
- **⚠ To verify at registration:** whether the *board* field is included in the bulk extract tables (it is on the per-school report cards; the documented extract schema mentions management/category/location but board needs confirming). If absent from bulk files, it can be scraped from report cards for a targeted subsample.
- **Role in this project:** (1) the **board × management cross-tab** — the empirical size of landmine #2 (ICSE≈private, state-board skews govt); (2) locating **off-diagonal cells** (private-unaided state-board vs. private-unaided CBSE) and where they coexist within the same block — the map of where a curriculum-within-management contrast *would* be identifiable if outcomes existed; (3) geographic granularity (state/district/block/village-location codes) supports within-area joins.

### 2.3 IHDS-II — SES-conditioned replication ✅ (fully public, start here while waiting on ASER)

- **What it is:** nationally representative panel, 42,152 households, 2011-12 ([ICPSR 36151](https://www.icpsr.umich.edu/web/ICPSR/series/507), free download in Stata/SPSS/R). Children 8–11 took short Pratham-designed reading/writing/arithmetic tests; plus the richest SES covariates of any dataset here.
- **Education module variables (verified against the [Education & Health questionnaire](https://ihds.umd.edu/sites/default/files/2022-08/ihds2ehq2.pdf)):** school type (Government / Govt-aided / Private / **Convent / Madrassa** / Open school); **medium of instruction** + from which standard English is taught; **fees actually paid last year** (incl. exam/lab fees) + books/uniform + transport + **private tuition spend**; **scholarship amount received**; government freebies (free fees / books / uniforms); *why did you choose this school* (codes include "affordable", "English medium", "only school available"); grade repetition count; days absent.
- **Board:** not in the household module ("board" appears in the questionnaire only for the electricity board). The [IHDS-2 Primary School Questionnaire](https://ihds.umd.edu/ihds-2-questionnaires) assesses one govt + one private *primary* school per village — board affiliation is largely a secondary-school concept, so no usable board variable.
- **Panel dimension:** IHDS-I (2004-05) tested children 8–11 who reappear in IHDS-II (2011-12) at ages 15–18 with enrolment/dropout/highest-grade outcomes — initial measured ability → later persistence, national scale (see §6).
- **Role:** replicate the ASER govt-vs-private gap with real SES conditioning (the triangulation rule: same comparison, different dataset, no score harmonization). Village/PSU identifiers allow within-community fixed effects.
- **Caveats:** 2011-12 vintage — state the caveat, don't stretch the inference. Check IHDS-3 (fielded ~2022-24) release status at ICPSR at Phase 1 time; if public, it supersedes the vintage caveat.

### 2.4 NAS 2021 — caveated aggregate cross-check only

- **What it is:** 3.4M students, 118k schools, classes 3/5/8/10, Nov 2021. Published as national/state/[district report cards](https://nas.gov.in/report-card/2021) and the [PARAKH dashboard](https://parakh.ncert.gov.in/nas-dashboard) with breakdowns by **management** (govt/aided/private), gender, social group, location.
- **No microdata:** NCERT states NAS does not provide individual student or school scores; there is no public unit-level file. Board is in the sampling frame (class 10 spans state boards and CBSE; central-govt schools ≈ CBSE — but that's the KV landmine #3: funding+curriculum bundled) yet published tables don't disaggregate by board.
- **Reliability (landmine, stated inline wherever NAS appears):** Johnson & Parrado, "Assessing the Assessments" — NAS state averages look inflated and state *rankings* are essentially uncorrelated with ASER and IHDS. Use only as a "does the direction replicate?" aggregate check, never as the outcome of record.

### 2.5 Young Lives 2016-17 school survey — the value-added prize, small and local

- **What it is:** secondary-school effectiveness study, ~9,000 Class 9 pupils in ~205 schools across Andhra Pradesh + Telangana, tested at the **beginning and end of the school year** (maths, functional English, transferable skills) — the only dataset in this audit measuring *learning growth*, which is exactly the selection-vs-teaching question. Sample deliberately stratified across school types: state government, private-aided, private-unaided, tribal/social-welfare ([design paper](https://www.gov.uk/research-for-development-outputs/the-design-of-the-2016-17-young-lives-school-survey-in-india), [country report](https://assets.publishing.service.gov.uk/media/5b9a9664e5274a13a7fd95f6/YL-School_Survey-CountryReport-India-17.pdf)).
- **Access:** UK Data Service, free registration, standard End User Licence. 2010-11 primary survey = SN 7478 (mirrored on the [World Bank microdata catalog](https://microdata.worldbank.org/index.php/catalog/2051)); the 2016-17 survey is archived in the same series — the Vietnam 2016-17 counterpart is [SN 8360](https://datacatalogue.ukdataservice.ac.uk/studies/study/8360), locate the India entry in the catalogue at registration.
- **⚠ To verify in documentation:** whether the head-teacher/school questionnaire records board affiliation explicitly. AP/TS secondary schools are predominantly state board with a private CBSE minority, so even a school-type variable may pin down board for most of the sample.
- **Bonus:** same states as the Muralidharan & Sundararaman voucher RCT — the benchmark comparison is in-sample by geography.
- **Caveats:** two states, not national; Class 9 only; ~205 schools limits off-diagonal cells.

---

## 3. The discount problem: fees *actually paid* vs. sticker price

Indian private schools price-discriminate heavily — sibling discounts, negotiated concessions, management quotas, scholarships, and the statutory RTE Section 12(1)(c) quota (25% of private-school entry seats reserved for disadvantaged children, fee-free). So "attends private school" ≠ "family pays full fee", and school type alone mismeasures the SES-composition term. Datasets that record the money side:

| Dataset | What it records | Discount identifiable? |
|---|---|---|
| **IHDS-II** | Fees *paid* last year per child (household-reported, i.e. post-discount) + scholarship amount + govt fee waivers + tuition/coaching spend — **alongside the child's test score** | ✅ Best single source: condition the govt-vs-private gap on fees actually paid, or use fee-paid within private as the SES-selection intensity measure |
| **NSS 75th (25.2)** | Course fees paid, itemized expenditure, whether education was **free / partially waived**, scholarship/stipend receipt, by institution type | ✅ National, recent (2017-18), fully public — no test scores though |
| **Young Lives** | Household education expenditure per child each round; school survey records the school's fee schedule | ✅ Panel version: paid-vs-list gap ≈ discount, and it can be tied to later scores |
| **ASER** | Only *whether* the child takes paid private tuition (no amounts, no school fees) | ❌ |
| **U-DISE+** | Nothing on money paid by households (RTE 12(1)(c) intake counts exist in some state modules — verify) | ◐ |

Design implication: in IHDS-II, run the private-school gap both ways — conditioning on SES *and* on fee actually paid. If the "private advantage" shrinks when fee-paid is controlled, that's the composition story showing through the discount channel.

## 4. The attrition taxonomy: five students walk into an ICSE school

The curriculum-vs-management question has a survivorship structure. Take five entrants to a high-fee, hard-curriculum school: **A** exits (can't afford), **B** exits (can't keep up with the curriculum), **C** stays via a discount and keeps up, **D** stays (can afford) but learns little, **E** stays and thrives — the standard intake-selection story. Cross-sectional comparisons only ever see C, D, E — the survivors — so the observed "board effect" is contaminated by *who exits*, not just who enters. What each margin needs data-wise, and where it exists:

| Student | Identifying signature | Where traceable |
|---|---|---|
| **A** — exits, financial | dropout with *adequate prior score* + reason = financial | **Young Lives panel** (scores observed *before* exit + coded leaving reasons); **NSS 75th** dropout reason codes ("financial constraints" is a literal code — national counts, no scores); IHDS discontinuation reasons |
| **B** — exits, curriculum | dropout with *low/declining prior score*; grade repetition before exit | **Young Lives panel**; **IHDS-I→II panel** (tested at 8–11 in 2005 → enrolment/highest grade at 15–18 in 2012); NSS reason codes ("unable to cope with studies / failure"); ASER over-age-for-grade as a cross-section proxy |
| **C** — stays via discount | continued enrolment + fees paid ≪ school norm, or scholarship/waiver > 0 | **IHDS-II** (fee paid + scholarship + score in one record); NSS waiver flags; Young Lives paid-vs-list gap; RTE 12(1)(c) quota children where flagged |
| **D** — stays, learns little | survivor with low *value-added* | **Young Lives 2016-17 school survey** (begin/end-of-year linked tests — this is exactly what it measures); Young Lives panel across rounds |
| **E** — stays, selected | intake SES × ability conditioning | All three microdatasets; the Muralidharan–Sundararaman voucher RCT is the clean benchmark (the voucher removes the affordability margin entirely, isolating E from A/C) |

**The board-linked version of attrition — the one new option found:** U-DISE+ publishes **grade-wise enrolment per school with board affiliation**. Cohort survival ratios (grade 8→9→10) computed by board give the aggregate footprint of A+B combined — including the documented "weeding" practice of schools holding back weak students before board exams. No individuals, no reasons, and cohort tracking across census years needs care (school switching, migration) — but it is the *only* attrition measure in existence that is linkable to board, and it's a genuinely novel descriptive exhibit: "how much of its entering cohort does each board shed before the board exam?"

## 5. Decision gate: which comparison is identifiable?

**(a) Curriculum within management (board contrast): ❌ not identifiable with public unit-level data.**
No dataset links board to a *test score* at the child/school level. The nearest approximations are: Young Lives *if* board is in the school questionnaire (small-N, AP/TS only); the U-DISE+ board-linked **cohort-survival funnels** of §4 (outcome = persistence, not learning); a **medium-of-instruction contrast within private schools** in IHDS-II (English-medium vs. regional-medium private as a curriculum-intensity proxy — imperfect, but unit-level, national, and score-linked); and NAS published aggregates by management (reliability-compromised, board only by proxy). U-DISE+ can show *where* the off-diagonal cells (private-unaided state-board vs. private-unaided CBSE) exist — that map, plus the board×management cross-tab, becomes the write-up's exhibit for **why the curriculum question can't be answered with existing public data**. That's a finding, not a failure; wear it per landmine section.

**(b) Management within village: ✅ identifiable, three-way triangulation.**
- **ASER** — raw govt-vs-private gap, then within-village; the raw→adjusted shrinkage is the headline (Phase 2).
- **IHDS-II** — same contrast, SES-conditioned + village fixed effects; fully public, so the pipeline can be built on it immediately.
- **Young Lives 2016-17** — the value-added version: does the private advantage survive conditioning on start-of-year score? Direct descriptive analogue of the Muralidharan-Sundararaman RCT result.
- **NAS 2021** — direction-only aggregate check, caveat inline.
- No score harmonization anywhere; replication of *pattern*, not pooling of scales (landmine #5).

**Verdict: proceed with the management version of the anchor question** ("does private school teach better or select better?"), with the board×management structure from U-DISE+ as the descriptive front half and the explicit demonstration that the board version is unanswerable as part of the contribution.

---

## 6. Immediate actions coming out of Phase 0

1. **Email ASER Centre** (contact@asercentre.org) requesting unit-level data for the latest available round(s) (2022/2024, fallback 2018) — longest lead time, send first.
2. **Register at ICPSR** and download IHDS-II (study 36151) *and IHDS-I (22626) for the panel linkage* — zero friction; Phase 1 SQL data model starts here.
3. **Register at UK Data Service**; download the Young Lives India 2016-17 school survey **and the household panel rounds**; check the school questionnaire for a board variable.
4. **Register at [microdata.gov.in](https://microdata.gov.in/NADA/index.php/catalog/151)** and download NSS 75th round Schedule 25.2 (fees, waivers, dropout reasons).
5. **Register at the U-DISE+ Data Sharing Portal**; confirm whether the affiliation-board field and grade-wise enrolment ship in the bulk extract (needed for the §4 board-attrition funnels).
6. **Skip** NAS microdata pursuit; bookmark the district report cards for the aggregate check.
7. Check **IHDS-3** release status at ICPSR before locking the vintage caveat into the write-up.

*Note: all registrations above require a human at the keyboard (OTP/email verification) — they're on you; everything downstream of the files landing in `data/raw/` can be automated. See [data/README.md](data/README.md) for the acquisition checklist.*

## Sources

- ASER: [survey page](https://asercentre.org/aser-survey/) · [assessment framework](https://img.asercentre.org/docs/Bottom%20Panel/Key%20Docs/aserassessmentframeworkdocument.pdf) · [FAQ](https://img.asercentre.org/docs/ASER%202022%20report%20pdfs/All%20India%20documents/FAQ/frequentlyaskedquestionsaboutaser.pdf) · [ASER 2024 national findings](https://asercentre.org/wp-content/uploads/2022/12/ASER-2024-National-findings.pdf)
- U-DISE+: [portal](https://udiseplus.gov.in/) · [data sharing portal](https://microdata.udiseplus.gov.in/) · [download guide (Education for All in India)](https://educationforallinindia.com/downloading-udise-data-on-school-education-samagra-shiksha-in-india/)
- IHDS: [IHDS-2 at ICPSR (36151)](https://www.icpsr.umich.edu/web/ICPSR/series/507) · [questionnaires](https://ihds.umd.edu/ihds-2-questionnaires) · [data guide](https://www.icpsr.umich.edu/sites/icpsr/posts/shared/ihds-ii-data-guide)
- NAS 2021: [nas.gov.in](https://nas.gov.in/) · [2021 report cards](https://nas.gov.in/report-card/2021) · [PARAKH dashboard](https://parakh.ncert.gov.in/nas-dashboard) · [PIB release](https://www.pib.gov.in/PressReleasePage.aspx?PRID=1828301)
- Young Lives: [India school survey](https://www.younglives.org.uk/india-school-survey) · [2016-17 design](https://www.gov.uk/research-for-development-outputs/the-design-of-the-2016-17-young-lives-school-survey-in-india) · [2016-17 India country report](https://assets.publishing.service.gov.uk/media/5b9a9664e5274a13a7fd95f6/YL-School_Survey-CountryReport-India-17.pdf) · [SN 7478 mirror (World Bank)](https://microdata.worldbank.org/index.php/catalog/2051) · [Vietnam 2016-17 = SN 8360](https://datacatalogue.ukdataservice.ac.uk/studies/study/8360)
