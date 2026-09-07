# Weekly study reporting from REDCap exports

R Markdown pipeline that turns weekly REDCap and learning management system
exports into recruitment, retention and survey completion reports for a
multi-site clinical trial.

The reports were run weekly during data collection and read by study staff and
site coordinators, so the emphasis is on catching problems early. Participants
overdue for a follow-up survey, sites falling behind on recruitment, and records
with missing timestamps all surface as tables rather than needing to be queried
by hand.

## Contents

- `Weekly-report-PCORI-AK.Rmd` builds the weekly operational report: recruitment
  and retention flow, per-site enrolment, survey completion status, and overdue
  follow-ups calculated against the most recent Friday.
- `PCORI_Updates.Rmd` produces the cumulative summary across the study period.

Both documents render to PDF, Word or HTML.

## Configuration

Data files live outside the repository. Point `PCORI_DATA_DIR` at your local
copy of the study data folder, in `.Renviron`:

```
PCORI_DATA_DIR=/path/to/DataTables
```

The scripts stop with a clear message if the variable is unset or the directory
does not exist, rather than failing later with an unhelpful path error.

## Data

No study data is included in this repository.

## Stack

R, `rmarkdown`, `knitr`, `tidyverse`, `redcapAPI`, `kableExtra`, `gtsummary`.
