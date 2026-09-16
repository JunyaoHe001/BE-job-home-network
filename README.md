# Belgian Job–Home Network Atlas

Interactive atlas of Belgian municipal home-to-work networks, 2015–2024, with population and employment stratification by age, sex, education, employment status and industry.

**Live atlas:** [junyaohe001.github.io/BE-job-home-network/atlas/](https://junyaohe001.github.io/BE-job-home-network/atlas/)

**Data compiled and harmonised by Junyao He.** Original data: **Vlaamse Arbeidsrekening (VAR), Steunpunt Werk**, with underlying administrative sources DWH AM&SB — KSZ and BISA. For access to the prepared research data or research collaboration, please contact **[Junyao He](mailto:j.he@rug.nl)**.

## Atlas

The atlas covers 565 Belgian municipalities and ten annual snapshots (2015–2024). It provides directional job–home links, municipal profiles, partner rankings, time trends and demographic/employment layers. The OpenStreetMap background requires no API key.

## Repository structure

- `site/atlas/` — published interactive atlas and browser assets.
- `site/index.html` — root redirect to `/atlas/`.
- `.github/workflows/deploy-pages.yml` — GitHub Pages deployment workflow.
- Future analysis code, notebooks and research outputs can be added separately without changing the published atlas.

## Data notes

Source cells below four workers may be suppressed. Missing links should therefore not automatically be interpreted as confirmed zeros. Group dimensions are separate source selections rather than joint demographic filters. The atlas uses a harmonised municipal geography for cross-year comparison.

## Deployment

GitHub Pages is configured to use **GitHub Actions**. A push affecting `site/**` publishes the static atlas automatically.

Background map: © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright).
