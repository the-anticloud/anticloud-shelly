# SHELLY

![license](https://img.shields.io/badge/license-license-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-consumer_appliances-lightgrey)

> Anticloud-hardened packaging of the upstream project `SHELLY` in category **CONSUMER APPLIANCES**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** CONSUMER APPLIANCES · **Upstream:** https://github.com/ALLTERCO/shelly-script-examples · **Upstream pin:** `2b4af48b4dee6d5ffa1303885b02497799d8817f` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

# Shelly Script Examples

This project contains example Shelly Script solutions.

Initial support for Shelly Script comes with firmware version 0.9, September
2021 for Gen2 Shellies based on ESP32.

## Who is this for?

This project is designed for:

- **Home automation enthusiasts** - Looking to extend Shelly device capabilities beyond the default features
- **Smart home integrators** - Building custom solutions with Shelly devices for clients
- **Developers** - Learning Shelly scripting through practical, working examples
- **IoT hobbyists** - Experimenting with BLE sensors, MQTT, LoRa, and other protocols
- **Energy-conscious users** - Implementing load shedding, power monitoring, and efficiency solutions

**Prerequisites:**
- Basic understanding of JavaScript
- Shelly Gen2 or Gen3 device with firmware 0.9+
- Access to the Shelly web interface or app for script deployment

## Documentation

- [Example Manifest](examples-manifest.json) - Machine-readable list of production examples, descriptions, and tags
- [Changelog](CHANGELOG.md) - See what's new
- [Contributing](CONTRIBUTING.md) - How to contribute to this project
- [Tools](tools/README.md) - Helper utilities for uploading scripts and validation
- [License](LICENSE) - Apache License 2.0
- [Shelly Script Documentation](https://shelly-api-docs.shelly.cloud/gen2/Scripts/ShellyScriptLanguageFeatures) - Official Shelly scripting docs

## Virtual Component Scripts

Runtime scripts that use Shelly Virtual Components should be self-contained. A user should be able to upload and start the script on a compatible device without manually creating the components first.

Use `snippets/virtual-components-helper.shelly.js` as the standard mechanism:

- Embed the helper as a normal code section in the standalone `.shelly.js` file. Do not copy the helper `@title`, `@description`, or `@status` metadata block into runtime scripts.
- Define one `VIRTUAL_COMPONENTS` manifest, or a small `buildVirtualComponentsManifest()` function when the script already has an `ENTITIES`/`COMPONENTS` table.
- Preserve fixed IDs when a README, dashboard, article, or companion script already documents `type:id` values.
- Put groups in the manifest and reference logical component keys, not raw strings such as `number:200`.
- Start polling, control handlers, HTTP requests, MODBUS reads, or BLE scanning only after `ensureVirtualComponents(...)` returns `ok === true`.
- Bind handles from the callback result, for example `readyVc.handles.soc`, instead of assuming the VC already exists.

The expected startup shape is:

```javascript
ensureVirtualComponents(VIRTUAL_COMPONENTS, function(ok, readyVc) {
  if (!ok) {
    print('ERROR: Virtual component setup failed');
    return;
  }

  bindVirtualComponents(readyVc);
  startApp();
});
```

This makes each script create missing VCs, reuse matching VCs, repair mismatched fixed-ID VCs, restore group membership, and bind handles before normal logic starts.

## Collections

- [The Pill](the_pill/README.md) - UART peripherals and hardware integrations
- [BLU Assistant](blu-assistant/README.md) - BLE device provisioning, configuration, and management scripts
- [Cury](cury/README.md) - Expressive light patterns and visual feedback for Shelly Cury devices

## project Layout

- [ble/](ble/README.md) - BLE/BLU sensors, buttons, and gateways
- [howto/](howto/README.md) - Minimal examples and tutorials
- [http-integrations/](http-integrations/README.md) - HTTP endpoints, notifications, and external services
- [lora/](lora/README.md) - LoRa send/receive and device control examples
- [modbus/](modbus/README.md) - MODBUS examples for RS485 add-ons and native MODBUS clients
- [mqtt/](mqtt/README.md) - MQTT and Home Assistant integrations
- [networking/](networking/README.md) - Provisioning and watchdog scripts
- [power-energy/](power-energy/README.md) - Load management, power thresholds, and monitoring
- [scheduling/](scheduling/README.md) - Scheduling, scenes, and orchestration
- [switch-input/](switch-input/README.md) - Input handling, switch behavior, and cover control
- [weather-env/](weather-env/README.md) - Weather and environmental sensor integrations

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Unknown (no standard manifest detected)** (manifests: none detected; scanned in UPSTREAM_CLONE)
- Top-level source layout: `ble/`, `blu-assistant/`, `cury/`, `howto/`, `http-integrations/`, `lora/`, `modbus/`, `mqtt/`, `networking/`, `power-energy/`, `pro_cb/`, `rgbw/`
- Snapshot size: **301 files**, **58027 lines of code** (measured; see Benchmarks)
- Primary languages: `.js` (169), `.md` (101), `.png` (13), `(none)` (5), `.json` (5), `.pdf` (3)
- Upstream commit pinned for this packaging: `2b4af48b4dee6d5ffa1303885b02497799d8817f`

---

## Installation

- **Developers** - Learning Shelly scripting through practical, working examples
- **IoT hobbyists** - Experimenting with BLE sensors, MQTT, LoRa, and other protocols
- **Energy-conscious users** - Implementing load shedding, power monitoring, and efficiency solutions

**Prerequisites:**
- Basic understanding of JavaScript
- Shelly Gen2 or Gen3 device with firmware 0.9+
- Access to the Shelly web interface or app for script deployment

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

This project contains example Shelly Script solutions.

Initial support for Shelly Script comes with firmware version 0.9, September
2021 for Gen2 Shellies based on ESP32.

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

- **Developers** - Learning Shelly scripting through practical, working examples
- **IoT hobbyists** - Experimenting with BLE sensors, MQTT, LoRa, and other protocols
- **Energy-conscious users** - Implementing load shedding, power monitoring, and efficiency solutions

**Prerequisites:**
- Basic understanding of JavaScript
- Shelly Gen2 or Gen3 device with firmware 0.9+
- Access to the Shelly web interface or app for script deployment

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Unknown (no standard manifest detected) |
| Manifests detected | none |
| Files in snapshot | 301 |
| Lines of code | 58027 |
| Dependency references | 0 |
| Upstream license | Apache-2.0 |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

- [Cury](cury/README.md) - Expressive light patterns and visual feedback for Shelly Cury devices

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# Contributing to Shelly Script Examples

First off, thanks for taking the time to contribute! ❤️

All types of contributions are encouraged and valued. See the [Table of Contents](#table-of-contents) for different ways to help and details about how this project handles them. Please make sure to read the relevant section before making your contribution. It will make it a lot easier for us maintainers and smooth out the experience for all involved. The community looks forward to your contributions. 🎉

And if you like the project, but just don't have time to contribute, that's fine. There are other easy ways to support the project and show your appreciation, which we would also be very happy about:
- Star the project
- Refer this project in your project's readme
- Mention the project at local meetups and tell your friends and colleagues

## I Have a Question

If you want to ask a question, we assume that you have read the available [Documentation](https://shelly-api-docs.shelly.cloud/gen2/Scripts/ShellyScriptLanguageFeatures).

Before you ask a question, it is best to search for existing [Issues](/issues) that might help you. In case you have found a suitable issue and still need clarification, you can write your question in this issue. It is also advisable to search the internet for answers first.

If you then still feel the need to ask a question and need clarification, we recommend the following:

- Open an [Issue](/issues/new).
- Provide as much context as you can about what you're running into.
- Provide project and platform versions (firmware version, device type), depending on what seems relevant.

We will then take care of the issue as soon as possible.

## I Want To Contribute

### Legal Notice 
When contributing to this project, you must agree that you have authored 100% of the content, that you have the necessary rights to the content and that the content you contribute may be provided under the project license.

### Reporting Bugs

#### Before Submitting a Bug Report

A good bug report shouldn't leave others needing to chase you up for more information. Therefore, we ask you to investigate carefully, collect information and describe the issue in detail in your report. Please complete the following steps in advance to help us fix any potential bug as fast as possible.

- Make sure that you are using the latest version.
- Determine if your bug is really a bug and not an error on your side e.g. using incompatible environment components/versions (Ma

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: Apache-2.0** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text

                                 Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

   TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

   1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original Apache-2.0 terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `Apache-2.0` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `SHELLY` (category: CONSUMER APPLIANCES)
- **Upstream URL:** https://github.com/ALLTERCO/shelly-script-examples
- **Pinned commit (SHA):** `2b4af48b4dee6d5ffa1303885b02497799d8817f`
- **Branch:** main
- **Pin provenance:** GitHub API commits/main. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`79059e023406641dbdcd055ce0f926de015c82b4d8d07f99d3c8eabc58513d12`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

