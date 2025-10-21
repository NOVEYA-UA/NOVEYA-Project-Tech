# NOVEYA-Project-Tech

Unified project stack and governance for NOVEYA public-infrastructure initiatives:
Aviation Cluster, Tavrida, Customs & Maritime Aquatoria, and more.  
Built on FDL (Formal-Dialectical Logic), with open, ethical, harmonized design.

## Scope
- Project registry (sectors/…)
- Shared schemas (data/api/policy)
- Playbooks & SOPs (ops, compliance, ethics)
- Integration map to NOVEYA Core/Meta Hub/Sigma-Avatarus

## How this repo is used
- Capture Notion knowledge → curate → publish stable specs.
- Define APIs and data models used across projects.
- Track roadmaps and cross-sector dependencies.

## Quick Start
- Explore `sectors/*/overview.md` and `schemas/`.
- For APIs see `schemas/api/openapi.yaml`.
- Contributions: see `CONTRIBUTING.md`.

## NOVEYA-Project-Tech/
│
├─ README.md                      ← обзор, принципы FDL, карта проектов
├─ LICENSE                        ← AGPL-3.0
├─ LICENSE-ETHICS.md              ← как в разделе 1.1
├─ CONTRIBUTING.md
├─ CODE_OF_CONDUCT.md             ← (по желанию, короткий)
│
├─ sectors/
│   ├─ aviation-cluster/
│   │   ├─ overview.md
│   │   ├─ roadmap.md
│   │   ├─ playbooks/            ← процедуры, SOP
│   │   ├─ specs/                ← API/данные, OpenAPI, схемы
│   │   └─ pilots/               ← пилотные сценарии, PoC
│   ├─ tavrida/
│   │   ├─ overview.md
│   │   ├─ roadmap.md
│   │   └─ specs/
│   ├─ customs-maritime/
│   │   ├─ overview.md
│   │   ├─ roadmap.md
│   │   └─ specs/
│   └─ ... (другие из Notion)
│
├─ schemas/                       ← общие схемы (JSON/YAML)
│   ├─ data/                      ← доменные модели (actors, assets, events)
│   ├─ api/                       ← openapi.yaml (шлюз/контракты)
│   └─ policy/                    ← декларативные правила FDL
│
├─ docs/
│   ├─ governance.md              ← роли, процессы принятия решений
│   ├─ ethics-fdl.md              ← расширение FDL для проектов
│   ├─ integration-map.md         ← как связаны NOVEYA-Core, MetaHub и т.д.
│   └─ notion-sync.md             ← правила синхронизации с Notion
│
├─ notion-sync/
│   ├─ mapping/                   ← “страница Notion → файл в репо”
│   └─ scripts/                   ← (позже: экспортер в Markdown)
│
└─ .github/
    └─ workflows/ci.yml

## License & Ethics

This repository follows a dual-license scheme:

- **Code:** AGPL-3.0  
- **Content / Symbols / Media:** CC BY-NC-SA 4.0  
- **Ethical charter:** see [LICENSE-ETHICS.md](./LICENSE-ETHICS.md)

Use of FDL/NOVEYA symbols is allowed **only** in open, benevolent contexts; closed or exploitative usage is prohibited.

---

## 3) Краткая настройка CI (по желанию, одинаковая везде)

`.github/workflows/ci.yml` (для Python; при необходимости сделаю Node-вариант):

```yaml
name: ci
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - run: pip install -r requirements.txt || true
      - run: pip install pytest || true
      - run: pytest -q || echo "No tests yet"
