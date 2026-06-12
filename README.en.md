🇫🇷 [Français](README.md) · 🇬🇧 [English](README.en.md)

# L-g-Chimio — version 2

**Integrated management of a research compound library and extract library, with cheminformatics and bioactivity.**

L-g-Chimio is a complete web application for managing a research laboratory's collections of compounds, whether obtained by synthesis or as natural extracts. Where these collections are usually scattered across spreadsheets, lab notebooks, freezer inventories and biological-result files, L-g-Chimio brings them together into a single, coherent and searchable system: one record ties together the **chemical structure**, the **physical stock**, the **provenance** and the **activity data** of a compound or an extract.

The application covers the entire life cycle of a sample. On the synthesis side, it manages **chemical compounds**: registration, 2D structures, descriptors and structural grouping. On the natural-products side, it tracks **extracts and their fractions**, from the source specimen (taxonomy, Nagoya / CITES compliance) through to bioassay-guided fractionation. And because chemistry only takes on its full meaning through what it produces biologically, it natively integrates **biological results** by target — classified using literature-based thresholds — and bridges all the way to **structure–activity analysis**.

At the heart of the system, a cheminformatics engine (**RDKit**) treats structures as genuine chemical objects — 2D rendering, descriptors, scaffolds, similarity — rather than mere images. Around it, everything is designed for everyday laboratory use: **physical storage** (vials, plates, tare weights), **ISO 9001-compliant audit logging**, **multi-team management** with access control, and an **interface available in 10 languages**. This repository is the **public release distribution channel** (changelog and version metadata); the application's source code is managed separately.

---

## At a glance

- 🧪 **Compound library** — a catalogue of molecules with 2D structures, descriptors and structural grouping.
- 🌿 **Extract library** — natural-product extracts and fractions, with taxonomy, regulatory compliance and fractionation.
- 🔬 **Bioactivity** — biological results by target, classified using literature-based thresholds, plus **bioassay-guided fractionation**.
- 📦 **Stock & traceability** — movements, labels/QR codes, plates, ISO 9001-compliant logging.
- 🌍 **10 languages** — fully internationalised interface.
- 🔐 **Security** — built following OWASP best practices, with per-team access control.

---

## Features

### Compound library (synthetic compounds)
- Complete compound record: identity, owner team, stock, references.
- **On-the-fly 2D structure rendering** via the RDKit cheminformatics engine (high-definition SVG).
- Molecular descriptors, **Murcko scaffolds**, **Butina clustering** and **structural-diversity** analysis.
- **Automatic enrichment** from PubChem (scheduled data updates).
- Management of **commercial chemicals** and their vials.

### Extract library (natural products)
- **Crude** extracts and **fractions** linked together (parent → fraction lineage).
- **Shared taxonomy** (family, genus, species, subspecies), organism part, extraction type and solvents.
- Tracking of source **specimens and samples**.
- **Regulatory-compliance** fields: Nagoya Protocol, CITES.
- Controlled vocabulary of **forms** (crude extract, fraction, essential oil, etc.) and units.

### Bioactivity & bioassay-guided fractionation
- Entry of **biological results** by target (enzyme, cell line, parasite…) and by laboratory/protocol.
- Multiple measures: **IC50, EC50, CC50**, % activity, % inhibition, **selectivity index**, with dedicated operators and units.
- **Activity classification** using assay-type thresholds drawn from the literature (cytotoxicity *NCI / Suffness-Pezzuto*, antimalarial *Berthi 2019*, antimicrobial *Kuete 2010*), with a generic scale otherwise.
- **Enrichment factor** parent → fraction: visualises how activity concentrates through fractionation — the core of bioassay-guided screening.
- Links to external target resources (UniProt, etc.) and **SAR analysis**.

### Import / Export
- Import from **Excel (.xlsx) or CSV** files for compounds, extracts, tare weights and biological results; **SDF** import for structures.
- **Multilingual header auto-detection**: a template downloaded and filled in any of the 10 languages is recognised automatically (and is accent-insensitive).
- Downloadable annotated templates; data exports.

### Stock, labels and traceability
- **Stock movements** and screening **plates**.
- Generation of **labels and QR codes**.
- **ISO 9001-compliant operation logging**.
- Dashboard, reports and synthesis ideas.

---

## Designed for the laboratory

- **Multi-team**, with data-visibility control by contract/team.
- **Interface in 10 languages**: French, English, Spanish, German, Italian, Portuguese, Dutch, Greek, Polish, Swedish.
- **Green chemistry**: a sustainability-footprint indicator on records.
- Designed to fit into an existing research environment (directory, backups, internal Git repository).

---

## Technical architecture

| Component | Choice |
| --- | --- |
| Language | **PHP 8.4**, **MVC** architecture (no Composer) |
| Database | **PostgreSQL 16** with the **RDKit cartridge** |
| Cheminformatics | **RDKit** (structure rendering, descriptors, scaffolds, clustering) |
| Internationalisation | 10 languages, no silent fallback |
| Security | Prepared statements (named placeholders), **CSRF** protection, nonce-based **CSP**, systematic output escaping |

---

## Releases

The detailed change log is available in [`CHANGELOG.md`](CHANGELOG.md). Metadata for the latest version is published in [`version.json`](version.json).

---

## Author & licence

Developed by **Laurent ROBIN** — CNRS / University of Orléans (ICOA, UMR 7311).
APP registration No. 99.75.3615
Distributed under the **CeCILL** licence.
