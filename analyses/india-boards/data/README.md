# Data acquisition checklist

**No microdata is in the repo yet.** Every source below sits behind a registration wall (OTP / email verification) or an email request, so a human has to fetch the files; once they land in `data/raw/` the pipeline takes over. `data/raw/` is gitignored — document provenance here instead of committing large files.

| # | Dataset | How to get it | Status |
|---|---|---|---|
| 1 | **ASER** unit-level (2022/2024, fallback 2018) | Email contact@asercentre.org — state research purpose. Longest lead time; send first | ☐ requested |
| 2 | **IHDS-II** (ICPSR 36151) + **IHDS-I** (ICPSR 22626) for the panel | Free ICPSR account → download Stata/R versions: https://www.icpsr.umich.edu/web/ICPSR/series/507 | ☐ |
| 3 | **NSS 75th rd. Sch. 25.2** (Education, 2017-18) | Free registration → https://microdata.gov.in/NADA/index.php/catalog/151 | ☐ |
| 4 | **Young Lives** 2016-17 India school survey + household rounds | Free UK Data Service account → search "Young Lives School Survey India 2016" (Vietnam counterpart is SN 8360; India entry is in the same series). 2010-11 primary survey mirror needs no UKDS account: https://microdata.worldbank.org/index.php/catalog/2051 | ☐ |
| 5 | **U-DISE+** bulk school-level extract | OTP registration at https://microdata.udiseplus.gov.in/ (250-char purpose statement). Verify board-affiliation field + grade-wise enrolment are in the extract | ☐ |
| 6 | ~~NAS 2021 microdata~~ | Not released — aggregates only via https://nas.gov.in/report-card/2021 | skipped |

Layout once files arrive:

```
data/
  raw/        ← as-downloaded, untouched, gitignored (note filename + download date below)
  processed/  ← cleaned outputs from sql/ and notebooks/, small files committable
```

## Provenance log

*(append one line per file as it arrives: date, source URL/email, exact filename, vintage)*
