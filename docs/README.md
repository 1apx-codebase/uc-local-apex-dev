# UC Local APEX Dev Documentation

This folder contains the documentation site for UC Local APEX Dev. The site uses Astro Starlight.

## Contents

- [Project Structure](#project-structure)
- [Documentation Pages](#documentation-pages)
- [Local Development](#local-development)
- [Writing Style](#writing-style)

## Project Structure

This section explains the main files and folders used by the documentation site.

| Name | Description |
| --- | --- |
| [`src/content/docs/`](src/content/docs/) | Documentation pages. |
| [`src/assets/`](src/assets/) | Images and other source assets. |
| [`public/`](public/) | Static files such as the favicon. |
| [`astro.config.mjs`](astro.config.mjs) | Site, sidebar, and plugin configuration. |

## Documentation Pages

This section lists the Markdown and MDX files that make up the documentation site.

| Name | Description |
| --- | --- |
| [Documentation Home](src/content/docs/index.mdx) | Introduces UC Local APEX Dev for first-time readers. |
| [Getting Started](src/content/docs/getting-started/index.mdx) | Explains how to install and start the local environment. |
| [Common Tasks](src/content/docs/getting-started/common-tasks.mdx) | Lists common container, ORDS, storage, account, import, and reset tasks. |
| [Creating Users](src/content/docs/getting-started/creating-users.mdx) | Explains how to create schemas and APEX workspaces. |
| [Backups](src/content/docs/getting-started/backups.mdx) | Explains backup and import commands. |
| [PL/SQL Debugging](src/content/docs/getting-started/plsql-debugging.mdx) | Explains how to prepare PL/SQL debugging. |
| [Install Apps or Scripts](src/content/docs/getting-started/install-apps-scripts.mdx) | Explains how to test APEX application exports and SQL scripts. |
| [Upgrade APEX](src/content/docs/migrations/upgrade-apex.md) | Explains how to upgrade APEX. |
| [Migrate to 25.1](src/content/docs/migrations/25-1.md) | Migration guide for release 25.1. |
| [Migrate to 25.2](src/content/docs/migrations/25-2.md) | Migration guide from 25.1 to 25.2. |
| [Migrate to 25.3](src/content/docs/migrations/25-3.md) | Migration guide from 25.2 to 25.3. |
| [Migrate to 26.1](src/content/docs/migrations/26-1.md) | Migration guide from 25.3 to 26.1. |
| [Migrate to 26.2](src/content/docs/migrations/26-2.md) | Migration guide from 26.1 to 26.2. |
| [Migrate to 26.3](src/content/docs/migrations/26-3.md) | Migration guide from 26.2 to 26.3. |
| [FAQ](src/content/docs/other/faq.md) | Answers common project questions. |
| [Podman on macOS](src/content/docs/other/podman-on-mac.md) | Explains how to use Podman on macOS. |

## Local Development

Run these commands from the `docs` directory.

| Name | Description |
| --- | --- |
| `npm install` | Installs documentation dependencies. |
| `npm run dev` | Starts the local documentation server. |
| `npm run build` | Builds the static documentation site. |
| `npm run preview` | Previews the built site locally. |

> **Note**
> Documentation pages use Markdown or MDX. Use MDX when a page imports Starlight components such as `Aside`.

## Writing Style

- Define product terms before you use them.
- Use numbered steps for procedures.
- Use tables for command options, parameters, and comparisons.
- Use callouts for notes, important warnings, and data-loss risks.
- Use monospace for commands, file paths, environment variables, and code.
