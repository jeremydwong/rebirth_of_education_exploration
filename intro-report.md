# Analyzing PISA Cross-country Education Performance

### Nordic (Norway, Sweden, Finland), North America (Canada, US), Asian (South Korea, Vietnam, India)
*Living document, v1.5 — June 2026. PISA data: 2022 round (latest full cycle; PISA 2025 results not yet published).*

---

## 1. Summary

In this document we establish 

- 2. Document PISA performance 
- 3. Interpret PISA's 500-pt scoring
- 4. Consider a general linear model of education (inspired by Lant Pritchett's 2013 Book)
- Consider the various terms and their impacts on the countries considered here

Our plans for this document include 

- tests of Lant's 6 causes in Indian schools by comparing performance between economically-and-regionally-similar schools

Among the important summary points are

- The Nordic countries' educational reputation is largely a legacy of 2000–2009; Finland is a good-but-no-longer-elite performer in steady decline since ~2006; Sweden is slightly above the OECD average after a crash and partial recovery; Norway is *below* the OECD average in math despite being the OECD's second-highest spender per student; What remains genuinely exceptional about the Nordics is not their average scores but **how little school choice matters within them** (§5) and **how weakly education predicts earnings** (§10)
- many countries benefit from selection of well-performing states, not representative of the country at large
- marginalized communities are largely exempt from national participation
- tests that (profoundly) gate post-secondary enrollment tend to cause much better educational performance
- spending does not well-predict performance; thus even considering testing performance, other factors remain critical

---

## 2. What PISA is, and how to read the numbers

**What PISA is.** The OECD's triennial assessment of **15-year-olds** — sampled by *age*, not grade (birth window 15y3m–16y2m; mostly Grade 10 in Canada, grades 9–11 elsewhere). Tests applied math, reading and science literacy — unfamiliar problems, not curriculum recall. ~690,000 students across 81 systems in 2022. Who gets *left out* of each country's sample matters more than most coverage of PISA admits — see §2.1.

**Rules of thumb — read these before the chart:**

- **Anchor:** scale set in 2000 with OECD mean = 500, SD = 100. Everything since floats against that anchor (OECD math mean is now 472). Within-country SD today ≈ 90.
- **1 school year** of learning at age 15 ≈ **15–20 points** (OECD's current framing; the old "30–40 points per year" rule is deprecated).
- **1 IQ-style point** ≈ 6.7 points (see §3.2).
- **Within one country:** median student → 95th percentile ≈ **150–165 points**; 10th → 90th percentile ≈ **230–260 points**. So the entire Norway–Korea gap (59 points) fits ~4× inside the spread of either country's own students.
- **Country means carry ±3–5 point confidence intervals** → single-digit gaps between countries are noise.
- **Effect-size calibration:** typical evaluated interventions (class size, tutoring, accountability reforms) move 5–20 points; rich-country gaps run 10–60 points; rich-vs-poor-country gaps run 100–250 points.
- **Proficiency levels:** Level 2 (~420+) = baseline "can participate in modern society"; Levels 5–6 (~607+) = can model complex problems. "%<L2" is the failure rate; "%≥L5" is the excellence rate.

<details>
<summary><b>Longer version (Pritchett / Hanushek / Caplan framing)</b></summary>

Lant Pritchett's core finding (*The Rebirth of Education*, 2013): enrollment converged globally, learning did not — "schooling ain't learning." Flat learning profiles mean a year of bad schooling adds nearly nothing, so the binding constraint in poor systems is not access or money. Hanushek & Woessmann's "knowledge capital" results: national *scores*, not years of schooling, predict long-run growth (≈1.5–2pp annual growth per national SD, with causality caveats). Caplan's signaling critique applies to *credentials*, not measured skills — which arguably makes PISA gaps more economically meaningful than attainment gaps. Countervailing caveats: enrolled-only sampling, the US 2022 response-rate miss, differential test effort (East Asian students try harder on a no-stakes test). These compress true gaps at the bottom but don't reorder the table.
</details>

### 2.1 Who is missing from each country's sample — exclusions, coverage, and whether it changes the conclusions

Three distinct leakage channels, often conflated:

1. **Formal exclusions** — students enrolled but exempted from testing (intellectual/functional disability, insufficient test-language proficiency). PISA caps this at 5%; several rich countries blow through it.
2. **Coverage** — 15-year-olds who aren't in the sampling frame at all because they've left school. Free points for countries with high dropout: their weakest kids were never testable.
3. **Frame choices** — countries deciding which schools or regions count as "the country."

**Canada — your memory is confirmed, and it's worse than remembered.** The official Canadian report states directly that <a href="https://www.cmec.ca/Publications/Lists/Publications/Attachments/438/PISA-2022_Canadian_Report_EN.pdf">no data were collected in the three territories or in First Nations schools</a> — i.e., on-reserve, federally/band-administered schools are outside the frame entirely, every cycle. On top of that, Canada's *formal* exclusion rate is chronically among the world's highest: <a href="https://amp.cbc.ca/news/canada/prince-edward-island/pei-pisa-exclusion-rate-1.3885189">7.5% nationally in 2015 — third highest and above the OECD's own ceiling — with PEI excluding 14.3% of eligible students (one in seven, the highest rate of any jurisdiction tested) and BC 11.1%</a>, mostly under the intellectual-disability category. Canada was also among the countries flagged in 2022 for missing one or more sampling standards, and peer-reviewed work (Anders et al. 2021) concluded that <a href="https://link.springer.com/article/10.1007/s11092-023-09416-3">the combination of high exclusion rates and relatively low response rates likely biases the Canadian PISA sample</a>. Honest magnitude estimate: on-reserve students are roughly 1–2% of the national cohort, and excluded special-needs students cluster in the left tail, so plausible inflation of Canada's mean is in the **single digits of points** — enough to narrow the gap to Finland, not enough to demote Canada from the upper tier. But it specifically flatters Canada's *floor* statistics (%<L2), which is exactly the metric §3.1 argues we should care about.

**Sweden — the same disease, immigration edition.** Sweden's National Audit Office concluded that <a href="https://link.springer.com/article/10.1007/s11092-023-09416-3">Sweden's 2018 exclusion rate did not follow OECD criteria and the results could have been significantly affected</a> — the surge came from classifying recently arrived refugee-background students as language-excludable. Part of Sweden's celebrated 2015→2018 "recovery" may therefore be a denominator effect. (The Sami minority in Sweden/Norway/Finland, by contrast, attends ordinary or sameskolor within the regular frame — no analogous exclusion.)

**United States** — the 2022 school response rate was 51% before replacement (63% after) versus the 85% standard; NCES's bias analysis argued the achieved sample was balanced on observables, which is what one says when one cannot check unobservables.

**China — the maximal frame choice.** "China" in PISA is **B-S-J-Z**: Beijing, Shanghai, Jiangsu, Zhejiang — four of the richest provinces, ~180M people presented as a country-topping super-entity. Within even those provinces, <a href="https://www.brookings.edu/articles/the-children-pisa-ignores-in-china/">hukou (residence-permit) rules exclude many migrant workers' children from the sampled schools</a> — the children of exactly the population that built those provinces' wealth. China's "world #1" status should be read as "elite-region China, minus its disadvantaged migrants."

**Vietnam — the coverage channel.** Vietnam's strong scores cover only the fraction of 15-year-olds still enrolled (NCES flags systems below 75% and below 50% coverage; Vietnam has hovered in the low band). Its 2018 results were withheld entirely for technical problems, and the OECD states its 2022 results aren't comparable to past cycles. The right reading survives but shrinks: enrolled urban-and-school-going Vietnam genuinely performs near OECD level; *all of Vietnam's 15-year-olds* would score meaningfully lower.

**India — the reverse twist.** The 2009 sample was two of India's *stronger* states, so unlike the cases above, the frame choice means the national truth is likely *worse* than the reported ~345.

**Does any of this reorder the table?** Mostly no, with two honest adjustments: (1) rich-country gaps of <10 points (Canada vs Finland, Sweden vs Spain) are within exclusion-bias territory and shouldn't be narrated as real; (2) the scores of high-dropout and frame-restricted systems (Vietnam, B-S-J-Z, 2009 India in reverse) are bounds, not estimates — Vietnam's is an upper bound on its cohort, India's an upper bound on its nation. The deeper point for this report: **exclusion is itself a policy choice that reveals what a system thinks the floor is.** Canada quietly removing its most disadvantaged population from the national scoreboard while ranking among the most equitable systems *on the sample it submits* is a small, polite version of Pritchett's camouflage problem (§4, β₂).

---

## 3. The charts

OECD averages: **Math 472 · Reading 476 · Science 485 · %<L2 math: 31% · %≥L5 math: 9% · Δ = −22**

### 3a. Performance (PISA 2022; India: PISA 2009+)

| Country | Math | Read | Sci | %≥L5 math | %<L2 math | **Net = %≥L5 − %<L2 (pp)** |
|---|---|---|---|---|---|---|
| 🇸🇬 Singapore | 575 | 543 | 561 | **41%** | **8%** | **+33** |
| 🇰🇷 South Korea | 527 | 515 | 528 | 23% | ~16% | **+7** |
| 🇪🇪 Estonia (ref.) | 510 | 511 | 526 | ~13% | ~15% | −2 |
| 🇨🇦 Canada | 497 | 507 | 515 | 13% | 22% | −9 |
| 🇫🇮 Finland | 484 | 490 | 511 | ~11% | 25% | −14 |
| 🇸🇪 Sweden | 482 | 487 | 494 | ~9% | 27% | −18 |
| 🇪🇸 Spain | 473 | 474 | 485 | ~6% | 27% | −21 |
| 🇻🇳 Vietnam | 469 | 462 | 472 | ~5% | ~28% | −23 |
| 🇳🇴 Norway | 468 | 477 | 478 | ~7% | 31% | −24 |
| 🇺🇸 United States | 465 | 504 | 499 | 7% | 34% | −27 |
| 🇮🇳 India — Tamil Nadu (2009) | 351 | 337 | 348 | ~0% | ~85% | ~−85 |
| 🇮🇳 India — Himachal Pradesh (2009) | 338 | 317 | 325 | ~0% | ~90% | ~−90 |

**Reading the Net column (and why negative is correct):** both percentages are within the *same* country — it's the share of that country's kids at excellence (Level 5+) minus the share below baseline (Level 2). Negative simply means more kids are failing than excelling, which is true everywhere except Singapore and Korea — even the OECD average is −22 (9% excellent, 31% failing). It is a *net balance of tails*, not a score gap. If you wanted the score-gap version — points between a country's high and low performers (P90 − P10) — that number is always positive and surprisingly uniform: roughly **230–260 points in nearly every country**, rich or poor (exact values: PISA 2022 Table I.B1.2.1). That uniformity is itself a finding: countries differ enormously in *where* their distribution sits, and very little in *how wide* it is.

### 3b. Inputs & structures

| Country | GDP/cap PPP (~) | Spend/student/yr (~) | Avg pts per $1k | Teacher selectivity (~) | Teacher union? | Performance pay? |
|---|---|---|---|---|---|---|
| 🇸🇬 Singapore | $140k | ~$15k | 37 | High — recruits from top third of cohort, MOE-managed | Yes (cooperative) | **Yes** — EPMS appraisal & bonuses |
| 🇰🇷 Korea | $60k | ~$21.5k | 24 | High — competitive entry, civil-service status | Yes | No — seniority scale |
| 🇪🇪 Estonia | $48k | ~$9.5k | **54** | Moderate, prestige rising | Yes | Partial — school-level discretion |
| 🇨🇦 Canada | $62k | ~$15k | 34 | Moderate | Yes — strong (ATA etc.) | No — grid by seniority + credentials |
| 🇫🇮 Finland | $64k | ~$12.5k | 40 | **Very high — ~10% acceptance, master's required** | Yes — OAJ, ~95% coverage | No |
| 🇸🇪 Sweden | $70k | ~$15.5k | 31 | **Low — teacher-ed admission standards collapsed post-1990s** | Yes — strong | Partial — individualized pay-setting since 1996 |
| 🇪🇸 Spain | $53k | ~$10.5k | 45 | Selective *at hiring* (oposiciones exam), not at training | Yes | No — fixed scales |
| 🇻🇳 Vietnam | $16k | ~$2.5k | **~190** | Moderate; low pay, informal tutoring income | State union only | No |
| 🇳🇴 Norway | $106k | ~$19.8k | 24 | Low-moderate — average pay, modest prestige | Yes — strong | No — centralized |
| 🇺🇸 US | $86k | ~$19k | 26 | Low — wide variation by state | Mostly yes | Rare — scattered merit-pay pilots |
| 🇮🇳 India | $11k | <$1k | n/a | Low — diploma-mill credentialing; chronic absenteeism | Yes — politically powerful | No |

GDP/capita: IMF PPP ~2024, rounded. Spending: government expenditure per school-level student, USD PPP, OECD *EAG 2025* (exact: Table C1.1). Teacher columns are characterizations from the comparative literature, not a single dataset — flagged in Open Items. "Pts per $1k" = 3-subject average ÷ spend: deliberately crude (see §9).

Quick reads across 3a+3b: teacher *selectivity* tracks performance far better than teacher *pay structure* — Finland (no performance pay, near-total unionization, elite selectivity) and Singapore (performance pay, cooperative union, elite selectivity) both work; Sweden (individualized pay, collapsed selectivity) and Norway (no performance pay, modest selectivity) both underperform. The union column is nearly uniform "yes" among high and low performers alike — it has no explanatory power in this sample. Selection into teaching is the live variable; compensation *structure* looks like a rounding error.

**India:** participated exactly once — PISA 2009+, via two reputedly strong states, ranked **72nd/73rd of 74**, beating only Kyrgyzstan. India signed up for the 2021/22 cycle (Chandigarh + central-government schools) and withdrew; there is no second data point. The average student in its showcase states scored below the **5th percentile** of the OECD distribution. ([EducationWorld](https://educationworld.in/india-opts-out-of-pisa-2022-prudence-or-cowardice/), [Leap Blog](https://blog.theleapjournal.org/2012/01/first-pisa-results-for-india-end-of.html))

**Vietnam caveat:** paper-based testing, lower cohort coverage, past comparability flags (2018 reading/science withheld). Read as "≈OECD-average math at 1/8 the income," not a precise rank.

### 3.1 Raising all boats vs. raising the lowest boats

One natural question about *any* service delivered to a population: what do you actually care about — **the average, the low performers, the high performers, or how close low and high are?** If you care about equality per se, you watch the high−low gap. If you care about everyone, you watch the average and the floor. These can point in different directions: a system could in principle buy a small gap by suppressing its top.

So the sharp question for our data is: **given a country's average, how does its spread behave?** The Net column (excellence rate minus failure rate) answers it, and the answer is unambiguous: **the net balance is almost a deterministic function of the average.** Singapore is +33; Korea +7; the rich-world pack sits at −9 to −27 in strict rank order of their means; India is ~−85. No country in the table bought a compressed spread by trading away its top, and no country grew a big top tail while abandoning its floor. Excellence rate and failure rate correlate at roughly −0.9 across PISA: **systems that teach well teach everyone.** (Extreme case: in Macao, the most *disadvantaged* students outscore the OECD *average* student.)

This validates the "raise all boats" framing with one refinement: across countries, **the floor moves more than the ceiling**. Going from Norway to Korea roughly halves the failure rate (31%→16%) while tripling the excellence rate (7%→23%) — both boats rise, the lowest rises most in absolute headcount. And decline works the same way in reverse: Finland's 2018–22 collapse was concentrated among low achievers. The implication for policy debates: inequality *metrics* (gaps, Ginis of scores) are symptom trackers. The target is the pair (%<L2 ↓, %≥L5 ↑), and empirically you don't have to choose.

Where systems do differ is *emphasis at the margin*: the Nordics historically bought an extremely high floor (§5: almost no bad schools) but produce thin elite tails (7–11% vs Korea's 23%). Canada is the rare Western system with a decent floor *and* a real tail.

### 3.2 IQ-style normalization (Singapore mean = 100, SD = 15)

Each country mean rescaled as `100 + (score − Singapore)/100 × 15`; one IQ-style point ≈ 6.7 PISA points. Read: *"the average student in X scores like the Nth-percentile Singaporean."*

| Country | Math | Reading | Science | 3-subj avg | ≈ Singapore percentile |
|---|---|---|---|---|---|
| 🇸🇬 Singapore | 100.0 | 100.0 | 100.0 | 100.0 | 50th |
| 🇰🇷 Korea | 92.8 | 95.8 | 95.1 | 94.6 | ~36th |
| 🇪🇪 Estonia | 90.3 | 95.2 | 94.8 | 93.4 | ~33rd |
| 🇨🇦 Canada | 88.3 | 94.6 | 93.1 | 92.0 | ~30th |
| 🇫🇮 Finland | 86.4 | 92.1 | 92.5 | 90.3 | ~26th |
| 🇺🇸 US | 83.5 | 94.2 | 90.7 | 89.5 | ~24th |
| 🇸🇪 Sweden | 86.1 | 91.6 | 90.0 | 89.2 | ~24th |
| 🇪🇸 Spain | 84.7 | 89.7 | 88.6 | 87.7 | ~21st |
| 🇳🇴 Norway | 84.0 | 90.1 | 87.6 | 87.2 | ~20th |
| 🇻🇳 Vietnam | 84.1 | 87.9 | 86.7 | 86.2 | ~18th |
| — OECD avg | 84.6 | 90.0 | 88.6 | 87.7 | ~21st |
| 🇮🇳 India TN/HP 2009 | ~66 | ~63 | ~64 | **~64.5** | ~1st |

Takeaways: (1) the whole rich-world pack spans ~3 IQ-style points (87–90) — most ranking anxiety is noise-trading; (2) the biggest intra-Nordic gap (Norway–Finland) ≈ 3 points — a good-vs-mediocre school district, not different civilizations; (3) **India is the only entry genuinely far away** — the Vietnam–India gap (~22 pts) is ~7× the Vietnam–Finland gap. *(Population means on a learnable skills test, not innate-ability measures; the rescaling is a communication device.)*

---

## 4. A proposed model of national PISA performance (speculative)

**First, what a linear model is.** It's just a recipe for predicting an outcome by adding up weighted ingredients. A toy example:

> Pizza delivery time ≈ β₀ + β₁·(distance) + β₂·(traffic) + β₃·(number of pizzas)

The **β's are coefficients — pure scaling factors** that say how much one unit of each ingredient moves the outcome. β₀ is the baseline (the time even a next-door delivery takes). A big β₁ means distance dominates; a β near zero means that ingredient barely matters and you can ignore it. Fitting a model = arguing about the sizes and signs of the β's.

Lant Pritchett's *The Rebirth of Education* implicitly proposes such a model for national learning: in his telling, almost all the weight sits on one ingredient — whether the *system* is genuinely organized around learning (his "starfish" features: open, locally operated, performance-pressured, professionally networked, technically supported, flexibly financed) — while the ingredients politicians love (spending, buildings, enrollment) carry β ≈ 0. He's right about poor countries. But his model omits at least two terms that matter among rich ones. Here's my fuller version:

**Score ≈ β₀ + β₁·(Teacher selectivity) + β₂·(Accountability coherence — Pritchett) + β₃·(High-stakes terminal exam) + β₄·(Private returns to skill) + β₅·(Family/effort culture) + β₆·log(Spending) + β₇·(Competition × Grading-anchor) + β₈·(Composition) + ε**

(ε is the leftover noise no model captures.)

| Term | What it measures | In Pritchett? | My prior on β | Notes |
|---|---|---|---|---|
| β₁ Teacher selectivity | Who gets to become a teacher (see chart 3b) | Partially ("professional networking") | **Strong +** | The most robust rich-country correlate. Finland's edge was always this, not the pedagogy tourists' favorites |
| β₂ Accountability coherence | Is the system pointed at learning, or at inputs/compliance/enrollment theatre? | **His core thesis** | **Strong +; dominant in poor countries** | Explains Vietnam (system genuinely aimed at learning) vs India (a "camouflage" system optimizing syllabus-completion) at similar incomes |
| β₃ Life-altering terminal exam | Suneung/gaokao-class exam gating valued futures | **No — his biggest omission** | **Moderate +, convex costs** | Within the Nordics, exam intensity ranks Finland > Sweden > Norway — matching their PISA order. Costs explode at the Korean extreme (hagwon arms race, wellbeing, maybe fertility) |
| β₄ Private returns to skill | Earnings premium × exam-gated access to it (§10) | No | **Moderate +** | The incentive to grind. Norway: OECD-minimum returns, softest exams, weakest Nordic scores despite top spending |
| β₅ Family/effort culture | Parental investment norms, tutoring, homework tolerance | No (treats as given) | **Strong +, slow-moving** | The embarrassing term: East Asian diaspora students outperform in *any* system, incl. Vancouver and Stockholm. May be crystallized exam history — 1,300 years of imperial examinations |
| β₆ log(Spending) | $/student | "more of the same ≠ better" | **+ until ~$8–10k PPP, then ≈ 0** | Vietnam→Spain range: matters. Spain→Norway range: flat (§9) |
| β₇ Competition × Anchor | Choice/vouchers, *interacted with* external grading anchors | Partially (his "open systems") | **+ when anchored; ≈0 or − when grades are the currency** | Sweden vs Alberta is the identifying contrast (§6) |
| β₈ Composition | Immigration mix, child poverty, sample coverage | No | Mechanical | Norway's 51-pt immigrant reading gap; Canada's points-selected immigration tailwind; Vietnam's coverage flattery |

**Interaction terms — the slightly more complicated bit.** β₇ is written as a *product* of two ingredients, not a sum. That's an interaction: the effect of competition *depends on* whether grading is anchored — choice with external exams helps; choice where schools issue their own currency invites inflation (Sweden). The model's most important interaction isn't even written in the equation: **β₃ × β₂**. A brutal exam only works if the base system beneath it functions. India is the proof: it has one of Earth's most savage exams (IIT-JEE, ~1% admit rate) *and* the worst measured base in the table, because an elite exam atop a system where ten-year-olds can't read moves the top 0.5% and nobody else. Anyone selling you a single-ingredient theory of education — *just* add exams, *just* add choice, *just* add money — is selling you a model with no interactions, and the data refuse it.

**Who loads where (speculative attribution):**
- **Korea 527:** β₃+β₄+β₅ maxed; β₁ high. Pays the convex costs of β₃.
- **Estonia 510:** the quiet champion — β₂ (coherent, outcome-focused, decentralized-but-measured) + β₁ rising + a real exam, at $9.5k/student. Proof the middle terms beat money.
- **Canada 506:** moderate-everything + β₈ tailwind + mild β₃ (provincial exams) + decent β₄.
- **Finland 484 ↓:** lived off β₁+β₂; decline plausibly = β₂ erosion (curriculum drift, digitalization) + β₅ erosion (boys' reading collapse), with β₃/β₄ always weak — no backstop when the engine sputtered.
- **Sweden 482:** β₇ misfire (unanchored), β₂ damage from 1990s reforms, β₁ collapse, β₈ shift; partial recovery as inspection tightened.
- **Norway 468:** the cleanest null result: β₆ maxed, everything else withheld. Money cannot buy what every other term refuses.
- **Vietnam ~469:** β₂ unusually high for income, β₃ real, β₅ Confucian-exam heritage, β₆ tiny. The anti-India.
- **India ~345:** β₂ ≈ 0 at the base (Pritchett's own diagnosis); β₃ present but multiplied by zero.

**A term nobody models:** *floor enforcement* — does anyone face consequences when a ten-year-old can't read? Old Finland (≈⅓ of students received special-ed intervention at some point) and today's Estonia are floor-enforcement systems; mechanically, that's why their %<L2 was tiny. Distinct from accountability-in-general, and possibly the single highest-leverage design choice (§13).

---

## 5. School-level variance — "how generalized is the system"

Cleanest single metric: **share of total math variation that is *between* schools** (PISA 2022 Vol. I, Fig. I.2.6 / Table I.B1.2.7):

- **OECD average: 32% between / 68% within.**
- **Finland ≤10%** (one of six: Iceland, Ireland, Denmark, Saudi Arabia, Uzbekistan). Norway low teens; Sweden high teens after 30 years of vouchers; Canada ~upper teens. (~values: verify against Table I.B1.2.7 before quoting.)
- Tracked systems (Germany, Netherlands, Hungary) ≈ 50%+: school = destiny.

In Finland/Norway, schools are near-interchangeable — the true meaning of "generalized." Performance differences live *inside* every school. Flip side: no elite schools pull the tail up — one reason Nordic L5/6 shares are thin. For Alberta: Sweden's vouchers raised sorting *from a very low base* and still sit below the OECD average — choice increased stratification; it did not create Germany.

Equity companion: SES explains ~15.5% of math variance OECD-wide (advantaged−disadvantaged gap = 93 points); Canada, Finland, Norway all below average on SES-dependence; France among the worst (21.5%).

---

## 6. School choice — Sweden as the maximal charter experiment (Alberta lens)

Sweden 1992: universal untargeted vouchers, **for-profit operators** (now running most independent schools), no top-up fees, ~31% of upper-secondary students in *friskolor*.

| Claim | Evidence |
|---|---|
| Steepest OECD PISA decline 2000→2012 | Fact; partial recovery after |
| Choice *caused* it | Contested: decline hit high-SES kids nearly as hard — wrong fingerprint for a segregation story ([Sanandaji/IFN](https://www.ifn.se/media/hmhphujb/2014-sanandaji-sweden-has-an-education-crisis-but-it-wasn-t-caused-by-school-choice.pdf)). Rivals: progressive-pedagogy reforms, teacher-status collapse, composition |
| Choice increased segregation | Well-supported: register data show voucher-school presence raises sorting by parental education/origin ([Brandén & Bygren 2022](https://journals.sagepub.com/doi/10.1177/00016993211068318)) |
| Independent schools outperform | On externally-marked tests, after controls (~1 yr of math, Heller-Sahlgren) — selection never fully purged |
| **Grade inflation** | Clearest failure: grades are the admission currency, schools compete for applicants → both sectors inflate |

**Alberta contrast:** non-profit charters, capped, and **diploma exams anchor 30% of Grade-12 marks** — neutralizing Sweden's main corruption channel. Sweden's lesson ≠ "choice fails"; it's *choice + for-profits + teacher-grade currency + weak inspection = predictable scoreboard corruption* (model term β₇).

---

## 7. Exam structure — who has the massive, life-altering test? ✅

| System | Gate to university | **Massive life-altering exam?** | Notes |
|---|---|---|---|
| 🇰🇷 Korea | Suneung (CSAT) | ✅✅ maximal | One day; planes grounded during the listening section |
| 🇨🇳 China (ref.) | Gaokao | ✅✅ maximal | The archetype |
| 🇻🇳 Vietnam | National HS graduation exam | ✅ | High stakes, national |
| 🇮🇳 India | Board exams + JEE/NEET elite tracks | ✅ for the elite track | Atop a non-functioning base — the β₃×β₂ interaction, §4 |
| 🇫🇮 Finland | **Matriculation exam** + university entrance exams | ✅ moderate | The country's *only* external standardized test |
| 🇪🇪 Estonia | State exams (riigieksamid) | ✅ moderate | External, mandatory |
| 🇨🇦 Alberta | Diploma exams (30% of mark) + GPA | ◐ mild | Anchored but diluted |
| 🇸🇪 Sweden | Teacher grades **or** Högskoleprovet (≥⅓ of seats) | ◐ optional, retakable | Safety-valve design |
| 🇪🇸 Spain | EvAU/Selectividad | ◐ moderate | Weight shared with GPA |
| 🇺🇸 US | GPA + (declining) SAT/ACT | ◐→❌ | Test-optional drift |
| 🇳🇴 Norway | Teacher-assigned grades (+ some external exam grades in diploma) | **❌** | Softest in the table |

Pattern: within the Nordics, exam intensity ranks **Finland > Sweden > Norway — exactly their PISA order**. Across the table, every ✅ system outperforms its income-and-spending peers *except* India — the exception that proves the interaction. Suggestive, not causal; Finland also differs on teacher selectivity. ([Nordic exams review, Springer 2025](https://link.springer.com/article/10.1007/s11092-025-09469-6))

---

## 8. Inequality — two different questions

**A) How unequal are the societies?** Split income from wealth; Sweden sits at opposite ends:

| | Income Gini (disposable, ~) | Wealth Gini (2023, UBS) |
|---|---|---|
| Norway | 0.26 | moderate-high (oil fund socializes capital) |
| Finland | 0.28 | 64 — largest European *increase* since 2008 (+21%) |
| Sweden | 0.28 | **75 — highest of 12 European countries measured** |
| Canada | 0.29–0.30 | ~72 |
| Spain | 0.32 | 57 |
| US | 0.39 | ~83 |

Sweden compresses wages while tolerating extreme capital concentration (no inheritance tax since 2005, no wealth tax since 2007). [OWID Gini chart](https://ourworldindata.org/grapher/economic-inequality-gini-index?country=SWE~NOR~FIN~CAN~ESP~KOR~VNM~USA~IND) · [UBS coverage](https://www.yahoo.com/news/wealth-inequality-changed-across-europe-040117325.html)

**B) How generalized is education?** Maximally: comprehensive untracked schooling to 15–16, free through university, no fee-charging elite sector — even Sweden's "private" schools must take the voucher as payment in full. §5's variance numbers are the quantitative expression. Strains: Finland's decile gap widening from the bottom; Norway's 51-point immigrant reading gap (23 after SES adjustment). Per §3.1: inequality *metrics* are downstream of the thing you actually care about — whether everyone is learning.

---

## 9. Spending per student — why it explains nothing here

(Data in chart 3b.) The reading: **Norway spends ~8× Vietnam per student for one fewer math point**; Estonia outscores every Nordic at half Norway's budget. Past ~$8–10k PPP the cross-country spending–score correlation ≈ 0 (standard OECD finding). Money binds at Vietnam→Spain levels; above that, §4's other terms dominate. The "pts per $1k" column is deliberately silly among rich countries (diminishing returns make Vietnam unbeatable) — its real use is against anyone claiming the fix is *more budget*. [EAG 2025 finance chapter](https://www.oecd.org/en/publications/2025/09/education-at-a-glance-2025_c58fc9ae/full-report/key-system-level-indicators-of-education-finance_178e2c40.html)

---

## 10. Lifetime earnings — the incentive story

Tertiary premium over upper-secondary (EAG 2025; OECD avg **+54%**): Norway **+18%** (OECD minimum) · Sweden +22–25% (2nd lowest) · Finland +40% · Spain ~+45% · Canada ~+50% · Korea ~+65–70% (chaebol premia on top) · US ~+70% · Chile/Colombia >+100%. In Sweden/Norway/Denmark an arts-humanities degree pays *less* than stopping after high school.

This is model term β₄: Norway pairs the OECD's weakest skill-incentive with its softest exams and gets the weakest Nordic results despite near-top spending; Korea and Vietnam pair big premia with exam-gated access — maximal grind incentive. Estonia, as always, ruins the monocausal version. [EAG 2025 earnings](https://www.oecd.org/en/publications/education-at-a-glance-2025_1c0d9c79-en/full-report/what-are-the-earnings-advantages-to-education_7a7e64e0.html) · [Statistics Sweden](https://www.scb.se/en/finding-statistics/statistics-by-subject-area/education-and-research-in-the-higher-education-sector/population-education-and-study-participation/analysis-and-statistics-concerning-education-of-the-population/pong/statistical-news/relative-earnings-from-an-international-perspective/)

---

## 11. Spain and orthographic transparency (the control you requested)

Spanish has one of Europe's shallowest orthographies; so does Finnish — and transparent spelling was a stock explanation for Finland's early reading dominance (Finnish kids decode in months vs ~2–3 years for English). The control verdict: **orthography can't carry the load.** Spain, equally transparent, reads at exactly the OECD average (474) — 16 below Finland, 33 below English-orthography Canada. Shallow orthography buys faster *decoding* in grades 1–2; PISA at 15 measures comprehension, where vocabulary, reading culture and instruction dominate. (It may still partly explain Finland's historically high *floor* — decoding failure is a major source of left-tail readers in English.)

---

## 12. Ready-made charts (OWID grapher — edit the `?country=` list, codes joined with `~`)

- Math over time: <https://ourworldindata.org/grapher/pisa-test-score-mean-performance-on-the-mathematics-scale?country=SWE~NOR~FIN~CAN~ESP~KOR~VNM~USA>
- Reading: <https://ourworldindata.org/grapher/pisa-test-score-mean-performance-on-the-reading-scale?country=SWE~NOR~FIN~CAN~ESP~KOR~VNM~USA>
- Science: <https://ourworldindata.org/grapher/pisa-test-score-mean-performance-on-the-science-scale?country=SWE~NOR~FIN~CAN~ESP~KOR~VNM~USA>
- Income Gini: <https://ourworldindata.org/grapher/economic-inequality-gini-index?country=SWE~NOR~FIN~CAN~ESP~KOR~VNM~USA~IND>
- Education spending (%GDP): <https://ourworldindata.org/grapher/total-government-expenditure-on-education-gdp?country=SWE~NOR~FIN~CAN~ESP~KOR~VNM~IND>
- Learning-adjusted years of schooling (the Pritchett-style metric): <https://ourworldindata.org/grapher/learning-adjusted-years-of-school-lays?country=SWE~NOR~FIN~CAN~ESP~KOR~VNM~IND>

---

## 13. Fable's answers (opinions clearly mine; speculation flagged)

### a) "What would you do if you were managing India's education system?"

From the model in §4 — India's binding constraint is β₂ ≈ 0 at the base, so almost everything popular (more spending, more EdTech, more elite institutes, even more exams) is leverage on the wrong term.

1. **Make foundational learning the only metric that matters for a decade.** One public, sample-based, un-gameable measurement: can every 10-year-old read a simple paragraph and do two-digit subtraction? (ASER already exists — make it the system's scoreboard.) District officials' careers ride on it. This is the floor-enforcement term.
2. **Teaching at the Right Level, everywhere.** Pratham's TaRL is among the most replicated RCT-validated interventions in development economics: group children by current level, not age-grade, for part of each day. India's curriculum is calibrated to the top decile and loses everyone else by grade 3 — Pritchett's "overambitious curriculum" diagnosis. Ban "syllabus completion" as a success metric.
3. **Attack teacher absenteeism before teacher quality.** Historically ~20–25% of public teachers absent on a given day in some states. You don't need Finland's teachers; you need teachers who show up. Biometric attendance tied to pay is crude and works.
4. **Don't fight low-cost private schools — anchor them.** ~40–50% of urban kids are already in them. Same external assessment, published results, parental visibility.
5. **Mother-tongue instruction in early grades.** Decoding failure in a prestige second language manufactures illiteracy.
6. **Explicitly do NOT:** chase IIT prestige (β₃ × 0), buy tablets, or copy Finland — importing Finnish *autonomy* without Finnish *selectivity* imports Norway's problems at Indian incomes.

### b) "How should people navigate a choice-vs-public-only system?"

For a **parent**: first ask which kind of system you're in (§5). In a low-variance system (Finland, Norway, most of Canada), between-school differences are small enough that chasing schools buys mostly commute time and anxiety — the highest-return investments are at home (reading volume, math talk, peers). In a high-variance system (Germany, much of the US, urban India), selection genuinely matters — but most of what looks like school quality is **peer composition, not instructional value-add**; a school that *selects* good students is not a school that *produces* them. Ask for value-added/growth data, not raw averages; and per Sweden's lesson, trust external exam results over school-issued grades — schools competing for applicants have an incentive to flatter you.

For a **policymaker**: §6 compresses to a design rule — *choice is safe roughly in proportion to how externally anchored the scoreboard is.* Vouchers + teacher-grade currency + for-profits + weak inspection was the worst available combination. Choice + external exams + no screening + published value-added captures most of the upside with the corruption channel closed.

### c) "How do you experiment with education tools without competition?"

Competition is one discovery mechanism, and a noisy one (parents observe composition, not value-add). A public monopoly can out-discover a market if it does what markets can't — **randomize**:

- **Central measurement, local method freedom** — "tight on outcomes, loose on means." Pritchett's starfish built *inside* a public spider; roughly Estonia's actual design (wide pedagogical autonomy, external state exams, everything published).
- **Run the system as a standing RCT platform.** With thousands of schools, a ministry can randomize curricula, phonics programs, phone bans, schedules at school level and read out effects in 1–2 years with more power than any market signal. (The phone-ban literature — Norway included — came from exactly such staggered natural experiments.) The honest framing: "we don't know which method is best, so your district will help find out."
- **Copy the discovery, not the average:** within any uniform system, the 95th-percentile *classroom* is years ahead of the median on identical funding. Instrument it (external assessment again), find the outlier teachers, codify, replicate. The cheap version of what competition is supposed to discover, without the sorting cost.
- The honest limit: none of this generates the *pressure* competition does. A public system that measures honestly but never acts — closes nothing, fires no one, changes no method — owns a very accurate diary of its decline. Norway approximately demonstrates this failure mode. Measurement must be wired to consequences somewhere, or it's β₂ theatre.

---

## Changelog
- **v1.5** — renamed/clarified the Net (= %≥L5 − %<L2) column with a note on why negative values are correct, plus the always-positive P90−P10 alternative; new **§2.1 on sampling exclusions** (Canada's territories + First Nations schools confirmed excluded; Canada/Sweden exclusion-rate breaches; US response rates; China's B-S-J-Z + hukou frame; Vietnam coverage; India's reverse case) and what survives the caveats.
- **v1.4** — rules of thumb moved above the charts (§2); chart split into 3a Performance (Net column) and 3b Inputs & structures (GDP/cap, spend, efficiency, teacher selectivity, union, performance pay); §3.1 rewritten around the average/floor/ceiling/spread framing; §4 given a gentle intro (toy model → β's → Pritchett → full model → interactions).
- **v1.3** — GDP/capita, spending, efficiency, L5/L1, Estonia & India rows; linear model; exam checkbox; Fable's answers (§13).
- **v1.2** — PISA definition & scale moved above chart; IQ-style Singapore-normalized table.
- **v1.1** — interpretation, between-school variance, orthography control, extra countries, OWID links.

## Open items / to verify before citing precisely
- P90−P10 score spreads ("~230–260 in nearly every country") — exact per-country values: PISA 2022 Vol. I Table I.B1.2.1.
- %≥L5 / %<L2 math values marked "~" — exact: PISA 2022 Vol. I Tables I.B1.5.x.
- **Teacher selectivity / union / performance-pay columns (3b)** — characterizations from comparative literature (OECD TALIS, EAG D3), not one dataset; Sweden's "individualized pay since 1996" and Singapore's EPMS are solid; others should be checked before quoting.
- Between-school variance per-country values (Table I.B1.2.7) — only OECD avg (32%) and the ≤10% group text-verified.
- India 2009+ state scores (TN 351/337/348, HP 338/317/325) — Walker/ACER PISA 2009+ report; double-check.
- GDP/capita & spending rounded; exact: IMF WEO, EAG 2025 Table C1.1.
- Korea earnings premium (~marked).
