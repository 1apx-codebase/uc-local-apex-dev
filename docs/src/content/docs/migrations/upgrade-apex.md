---
title: Upgrade APEX
description: Upgrade Oracle APEX in UC Local APEX Dev.
sidebar:
  order: 1
---

Use this guide to upgrade Oracle APEX in an existing UC Local APEX Dev environment. APEX is the application development platform served by ORDS.

## Contents

- [Before You Begin](#before-you-begin)
- [Upgrade APEX in 26.2 or Later](#upgrade-apex-in-262-or-later)
- [Upgrade APEX Before 26.2](#upgrade-apex-before-262)
- [Fix Browser Cache Errors](#fix-browser-cache-errors)

## Before You Begin

This section helps you choose the correct upgrade method.

| Name | Description |
| --- | --- |
| `26.2` or later | Use `./scripts/upgrade-apex.sh`. |
| Earlier than `26.2` | Upgrade APEX manually. |

> **Important**
> Back up your schemas, workspaces, applications, and ORDS modules before you upgrade APEX.

## Upgrade APEX in 26.2 or Later

This section uses the project script to download APEX, run the installer, copy images, and reapply Internal workspace settings.

1. Run the upgrade script.

   ```bash
   ./scripts/upgrade-apex.sh
   ```

2. Wait for the script to finish.
3. Open APEX and verify that your workspaces still load.

## Upgrade APEX Before 26.2

This section gives the manual upgrade flow for older project versions.

1. Download the latest APEX ZIP file with `curl`.

   ```bash
   curl -fLO https://download.oracle.com/otn_software/apex/apex-latest.zip
   ```

   Or use `wget`.

   ```bash
   wget https://download.oracle.com/otn_software/apex/apex-latest.zip
   ```

2. Unzip the file.

   ```bash
   unzip apex-latest.zip
   rm apex-latest.zip
   rm -rf ./META-INF || true
   ```

3. Change into the APEX directory.

   ```bash
   cd apex
   ```

4. Run the APEX installer.

   ```bash
   sql -name local-23ai-sys @apexins.sql TBS_APEX TBS_APEX TEMP /i/
   exit;
   ```

5. If you are still on a 23ai version that uses `SYSAUX`, run this installer command instead.

   ```bash
   sql -name local-23ai-sys @apexins.sql SYSAUX SYSAUX TEMP /i/
   exit;
   ```

6. Return to the project root.

   ```bash
   cd ..
   ```

7. Replace the APEX images.

   ```bash
   rm -rf ./apex-images || true
   cp -r ./apex/images ./apex-images
   ```

## Fix Browser Cache Errors

This section explains what to do if APEX reports outdated files.

If your browser shows a popup that files are outdated, clear your browser cache and reload APEX.
