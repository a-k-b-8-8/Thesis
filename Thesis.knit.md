---
title: "Thesis"
---



## Quarto

Quarto enables you to weave together content and executable code into a finished document. To learn more about Quarto see <https://quarto.org>.



::: {.cell}

```{.r .cell-code}
library(tidyverse)
```

::: {.cell-output .cell-output-stderr}

```
── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.4     ✔ readr     2.1.5
✔ forcats   1.0.0     ✔ stringr   1.5.1
✔ ggplot2   3.5.1     ✔ tibble    3.2.1
✔ lubridate 1.9.3     ✔ tidyr     1.3.1
✔ purrr     1.0.2     
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```


:::
:::

::: {.cell}

```{.r .cell-code}
gen_con <- read_csv("gen_con_status.csv")
```

::: {.cell-output .cell-output-stderr}

```
Rows: 154 Columns: 13
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (11): Participant, Signature_Date, Ratification_Type, Ratification_Year,...
dbl  (2): Signatory_Status, Ratification_Status

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```


:::

```{.r .cell-code}
tmk <- read_csv("edited_tmk_annual_release_1.2.csv")
```

::: {.cell-output .cell-output-stderr}

```
Rows: 476 Columns: 8
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (1): primary.location
dbl (7): year, pl.ccode, tmk.onset, genpol.onset, genpol.ongoing.sum, tmk.on...

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```


:::
:::

::: {.cell}

```{.r .cell-code}
gen_con |>
  left_join(tmk, by = join_by(Participant == primary.location))
```

::: {.cell-output .cell-output-stdout}

```
# A tibble: 521 × 20
   Participant Signatory_Status Signature_Date Ratification_Status
   <chr>                  <dbl> <chr>                        <dbl>
 1 Afghanistan                0 N/A                              1
 2 Afghanistan                0 N/A                              1
 3 Afghanistan                0 N/A                              1
 4 Afghanistan                0 N/A                              1
 5 Afghanistan                0 N/A                              1
 6 Afghanistan                0 N/A                              1
 7 Afghanistan                0 N/A                              1
 8 Afghanistan                0 N/A                              1
 9 Afghanistan                0 N/A                              1
10 Afghanistan                0 N/A                              1
# ℹ 511 more rows
# ℹ 16 more variables: Ratification_Type <chr>, Ratification_Year <chr>,
#   In_Effect_IX_Reservation <chr>,
#   `Historical Reservation Made to article IX no longer in effect` <chr>,
#   `Reservation withdrawn year` <chr>,
#   `Reservation Made at Same Time as Ratification and or confirmed upon succession` <chr>,
#   `Successor State Entry` <chr>, `State System Membership Year` <chr>, …
```


:::
:::

