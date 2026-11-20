# TAF templates

The templates are listed in the governance
[templates.csv](https://github.com/ices-eg/wg_wgtafgov/blob/master/docs/_taf/site/boot/initial/data/templates.csv),
and their progress is shown on the
[template status page](https://ices-eg.github.io/wg_WGTAFGOV/status/templates.html).
All are in `ices-tools-dev`. Notes are from the repositories as of 2026-11-20;
the SAM entry describes its `dev` branch.

## Choosing

| Situation | Template |
|---|---|
| Age-based, SAM with the stockassessment package | SAM |
| Age-based, SAM already run on stockassessment.org | SAMfromSA |
| Age-based, SAM with FLR | FLSAM |
| Stock Synthesis | SS3 |
| Multispecies or sandeel, smsR | SMS |
| Surplus production, SPiCT | Spict |
| Category 3: rfb, rb or chr rule | Category3 |
| Category 5: catch-based advice | Category5 |
| F-based reference points | Fsquared |

## The templates

| Template | Repository | Example | Notes |
|---|---|---|---|
| SAM | `SAM_taf_template`, branch `dev` | ple.27.7d, 2026 | Reads either set of Lowestoft files (SAM-ready, or landings and discards separately), `.dat` or `.txt`. Fit with `model.cfg`, retrospective, leave-one-out, residuals, optional jitter; forecast with catch options (`nosim` setting); FLStock; SAG upload file (CSV); ASD upload file (XML); DATSU checks of both. Reference points, TAC and stock information are placeholders in `boot/initial/data`, with typed fallbacks in the scripts. Not yet: survey CVs as weights, forecast-year biology, change in advice. README with data flow diagrams. |
| SAMfromSA | `SAMfromSA_taf_template` | Faroe Plateau cod | Boot scripts download data and configuration from stockassessment.org, which is no longer online, so it cannot boot. Fit, retrospective, leave-one-out, forecast, FLStock, and Word, HTML and Quarto reports. |
| SESAMfromSA | `SESAMfromSA_taf_template` | | Empty: README only. |
| FLSAM | `FLSAM_taf_template` | Lowestoft files | Fit, retrospective and Mohn's rho. The top-level `boot.R` installs software [C6]. The example data mix two stocks: `cn` and `cw` are Faroese cod (1959–2024, ages 1–10), the rest greater silver smelt (1995–2024, ages 5–21). |
| SS3 | `SS3_taf_template` | Sardine | Runs SS3 with jitters and a retrospective. Forecast over F multipliers; FLStock with ss3om. The SS3 executable is in `boot/initial/software`. `report.R` is empty. |
| SMS | `SMS_taf_template` | Sandeel area 1r, 2026 | smsR. Retrospective and forecast table. No `output.R`. |
| Spict | `Spict_taf_template` | NEA golden redfish | SPiCT with management scenarios. Uses `bootstrap/`. Step-by-step instructions to adapt it in the README. |
| Category3 | `Category3_taf_template` | | Uses cat3advice. Each top-level script dispatches to `_rfb`, `_rb` or `_chr`. No `boot` folder in the repository. |
| Category5 | `Category5_taf_template` | Sandeel area 6, 2019 | SAG XML with icesSAG, and a Word report. Uses `bootstrap/`. No `model.R`. |
| Fsquared | `Fsquared_taf_template` | | Reference points with the FLR mse packages. No `data.R` or `report.R`. |

Not yet made: Nephrops, national estimation.

Older versions of the Category 3, Category 5 and SAM examples are in
`ices-taf-dev` (`ices_cat_3_template`, `ices_cat_5_template`,
`wiki-example-stockassessment`), linked from the TAF wiki. Prefer the
`ices-tools-dev` templates.
