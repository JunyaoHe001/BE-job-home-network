# Belgian Job–Home Network

An interactive atlas of Belgian municipal home-to-work networks, 2015–2024, with age, sex, education, employment-status and industry layers.

**Data compiled and harmonised by Junyao He.** Original data: **Vlaamse Arbeidsrekening (VAR), Steunpunt Werk**, with underlying administrative sources DWH AM&SB — KSZ and BISA. For access to the prepared research data and research collaboration, please contact **[Junyao He](mailto:j.he@rug.nl)**.

## Atlas

Permanent atlas path: **[BE-job-home-network/atlas/](https://junyaohe001.github.io/BE-job-home-network/atlas/)**. This becomes available when GitHub Pages is enabled and the deployment workflow succeeds. The site root forwards visitors to `/atlas/`.

The map covers 565 municipalities and 59 separate population or employment groups over ten years. It includes municipal profiles, directional links, partner rankings, time trends and resident population context. The OpenStreetMap background requires no API key. A municipal-boundaries-only background is also available.

## Repository layout

| Path | Purpose | Published to Pages? |
| --- | --- | --- |
| `web/` | React/TypeScript atlas source, build configuration and compact visualisation data archives | Source: no; compiled output only |
| `site/atlas/` | Reviewed, compiled browser assets | Yes, at `/atlas/` |
| `site/index.html` | Redirect to the atlas | Yes, at the site root |
| `analysis/` | Future formal statistical/network analysis scripts | No |
| `notebooks/` | Future research notebooks | No |
| `data/raw/` | Local original research inputs; large raw files are ignored | No |
| `data/processed/` | Future analysis-ready tables and codebooks | No |
| `results/` | Future research tables, figures and reports | No |
| `docs/` | Data definitions, provenance and repository documentation | No |
| `scripts/` | Reproducible atlas packaging and validation | No |

The deployment workflow assembles a dedicated `_site/` directory. It never publishes the repository root, research notebooks, raw data or analysis outputs. Changes confined to research directories do not trigger a map deployment.

## Data and interpretation

See [data notes](docs/data-notes.md). The source suppresses cells below four workers. Missing links are not confirmed zeros. Group dimensions are separate source selections and cannot be combined into joint demographic filters. Non-age groups cover ages 20–64. Resident population context is available for 2017–2024. All years use the matched 2025 municipal geography.

The compact archives under `web/data/` contain only the prepared atlas data. They are divided by year, with shared geography and time series in `common.zip`. The original research download is not duplicated in this repository. Archive hashes are recorded in `web/data/manifest.json`.

## Local development

```sh
python3 scripts/restore_web_data.py
cd web
pnpm install --frozen-lockfile
pnpm dev
```

After editing the atlas, build and record the reviewed browser assets from the repository root:

```sh
pnpm --dir web build
python3 scripts/stage_web_build.py
python3 scripts/prepare_pages.py
python3 -m http.server 8000 --directory _site
```

Preview at `http://localhost:8000/atlas/`. Commit both the source changes and the updated `site/atlas/` build. Deployment verifies the source/build manifest to prevent stale browser assets being published. No Node installation is needed in the deployment job itself.

## GitHub Pages setup

In **Settings → Pages → Build and deployment → Source**, select **GitHub Actions**. Then run or re-run **Deploy Belgian atlas** in Actions. The workflow publishes only the assembled `_site/` directory.

Third-party software notices are retained in [docs/third-party-notices.txt](docs/third-party-notices.txt). Municipal geometry derives from Statbel through [bmesuere/belgium-topojson](https://github.com/bmesuere/belgium-topojson). Background map: © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright).
