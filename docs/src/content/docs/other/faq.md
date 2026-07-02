---
title: FAQ
description: Frequently asked questions about UC Local APEX Dev.
sidebar:
    order: 1
---

Use this page for short answers to common questions. For installation steps, see [Getting Started](/products/uc-local-apex-dev/docs/getting-started/).

## Contents

- [Why use UC Local APEX Dev instead of another compose file?](#why-use-uc-local-apex-dev-instead-of-another-compose-file)
- [Can I modify ORDS settings?](#can-i-modify-ords-settings)
- [How do I upgrade the database?](#how-do-i-upgrade-the-database)
- [How do I upgrade ORDS?](#how-do-i-upgrade-ords)
- [How do I patch APEX?](#how-do-i-patch-apex)

## Why use UC Local APEX Dev instead of another compose file?

UC Local APEX Dev includes migration guides and task scripts in addition to container configuration.

| Name | Description |
| --- | --- |
| Migration guides | Version-specific instructions for database, APEX, and ORDS changes. |
| Task scripts | Commands for creating users, backing up data, clearing schemas, and testing installs. |

## Can I modify ORDS settings?

Yes. The setup creates an `ords-config` folder in the project root.

1. Edit the files in `ords-config`.
2. Restart the ORDS container.

For details, see [ORDS Configuration](/products/uc-local-apex-dev/docs/getting-started/common-tasks/#ords-configuration).

## How do I upgrade the database?

Use the migration guide for your target project version. Database and container image compatibility can change between releases.

Before you migrate:

- Read the full migration guide.
- Back up your schemas and workspaces.
- Back up any schemas or workspaces that were not created by this project.
- Check the [GitHub repository](https://github.com/United-Codes/uc-local-apex-dev) for newer release notes.

## How do I upgrade ORDS?

Use the migration guide for your target project version. ORDS is Oracle REST Data Services, the service that serves APEX and REST endpoints.

If you are experienced and want to test a different ORDS image yourself, edit `docker-compose.yml`. Available ORDS images are listed in the [Oracle Container Registry](https://container-registry.oracle.com/ords/ocr/ba/database/ords).

## How do I patch APEX?

This section describes the manual APEX patch flow.

> **Important**
> APEX patch set bundles may require a valid Oracle support account.

1. Open the [APEX downloads page](https://www.oracle.com/tools/downloads/apex-downloads/).
2. Select **Patch Set Bundle**.
3. Sign in with your Oracle account.
4. Download the patch ZIP file.
5. Unzip the file.
6. Open a terminal in the unzipped patch directory.
7. Run the patch script.

   ```bash
   sql -name local-23ai-sys @catpatch.sql
   ```

8. Copy the updated images into the project.

   ```bash
   cp -r ./images/* {path_to_your_cloned_repo}/apex-images
   ```

> **Note**
> The example uses `local-23ai-sys` because this FAQ was written for an older project version. Use the SYS connection name that matches your installed version, such as `local-26ai-sys`.
