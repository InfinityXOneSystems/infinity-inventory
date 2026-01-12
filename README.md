# Infinity Inventory Sync

Automated synchronization system for InfinityXOneSystems repository inventory.

## Overview

This system keeps Google Drive synchronized with GitHub repositories:
- **Source of Truth:** GitHub repositories
- **Mirror:** Google Drive /INVENTORY/
- **Sync Frequency:** Daily at 00:00 UTC

## Structure

```
/INVENTORY/
├── 00_MASTER_INDEX/
│   ├── MASTER_REPO_INVENTORY.xlsx
│   └── MASTER_REPO_INVENTORY_README.doc
├── 01_REPOS/
│   └── <repo-name>/
│       ├── 01_STRUCTURE/folder_inventory.xlsx
│       ├── 02_CODE_INDEX/code_inventory.xlsx
│       ├── 03_DOCS/
│       └── README.doc
├── 02_SYNC_SYSTEM/
│   ├── sync_architecture.doc
│   ├── sync_rules.doc
│   └── sync_audit_log.xlsx
└── 99_ARCHIVE/
```

## Sync Rules

1. GitHub ALWAYS wins conflicts
2. Artifacts are REGENERATED, not hand-edited
3. Every sync updates timestamps
4. Failures are visible, not silent
5. No repo exists without inventory folder

## Setup

1. Add `GH_TOKEN` secret with GitHub PAT
2. Add `RCLONE_CONFIG` secret with rclone configuration
3. Enable GitHub Actions

## Manual Sync

Run workflow manually from Actions tab or:
```bash
python scripts/sync.py
```
