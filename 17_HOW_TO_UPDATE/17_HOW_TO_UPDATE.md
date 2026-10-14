# How to Update — SHELLY

**Project:** `SHELLY`
**Category:** CONSUMER_APPLIANCES
**Domain:** consumer appliances and IoT
**Date:** 2026-10-07

---

## Update Procedure

### Checking for Updates
```bash
SHELLY --version
SHELLY check-update
```

### Applying Updates
```bash
pip install --upgrade SHELLY
```

### Rolling Back
```bash
pip install SHELLY==<previous-version>
```

### Update Policy
- **Security updates:** Applied immediately
- **Feature updates:** Monthly release cycle
- **Breaking changes:** 6-month deprecation notice

## Verification

All 16 checks PASS. Evidence: `ISOLATED_LAB_RESULTS/03_Result_Register.md`.
