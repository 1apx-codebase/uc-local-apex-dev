# UC Local APEX Dev

UC Local APEX Dev creates a local Oracle APEX development environment on your computer. It runs Oracle Database Free, Oracle APEX, and Oracle REST Data Services (ORDS) in containers. It also includes scripts for common local development tasks.

## Contents

- [Features](#features)
- [Documentation](#documentation)
- [Source Code Contents](#source-code-contents)
- [Contributing](#contributing)
- [Special Thanks](#special-thanks)

> **Caution**
> This project is for local development only. Do not use it for production. It stores passwords in plain text and relaxes security settings to make local development easier.

## Features

This section summarizes the main features of UC Local APEX Dev.

- Start and stop a local Oracle Database, APEX, and ORDS environment.
- Create database schemas and APEX workspaces.
- Save connections for SQLcl and the VS Code SQL Developer extension.
- Back up and restore schemas, workspaces, applications, and ORDS modules.
- Test APEX application installs and SQL scripts in a clean schema.
- Use PL/SQL debugging from VS Code SQL Developer.
- Run ORDS with local HTTPS by using self-signed certificates.

## Documentation

Use the documentation site for setup steps, task guides, and migration guides:

[UC Local APEX Dev Documentation](https://www.united-codes.com/products/uc-local-apex-dev/docs/)

Start here:

- [Getting Started](https://www.united-codes.com/products/uc-local-apex-dev/docs/getting-started/)
- [Common Tasks](https://www.united-codes.com/products/uc-local-apex-dev/docs/getting-started/common-tasks/)
- [Backups](https://www.united-codes.com/products/uc-local-apex-dev/docs/getting-started/backups/)
- [Migration Guides](https://www.united-codes.com/products/uc-local-apex-dev/docs/migrations/25-3/)

## Source Code Contents

This section lists the source files in the repository and what each file is for. Generated files are not included.

| Name | Description |
| --- | --- |
| `.github/fixtures/test_install.sql` | SQL fixture used by GitHub Actions tests. |
| `.github/workflows/test-clean-install.yml` | GitHub Actions workflow for clean install tests. |
| `.github/workflows/test-db-upgrade.yml` | GitHub Actions workflow for database upgrade tests. |
| `.gitlab-ci.yml` | GitLab CI configuration. |
| `docker-compose.yml` | Defines the database and ORDS containers. |
| `docs/README.md` | Explains how to work on the documentation site. |
| `docs/astro.config.mjs` | Configures the Astro Starlight documentation site. |
| `docs/build-static-website.sh` | Builds the static documentation site. |
| `docs/src/content.config.ts` | Defines the Starlight content configuration. |
| `install.sh` | Runs the full local installation flow. |
| `local-26ai.sh` | Provides the main command wrapper for local tasks. |
| `readme.md` | Introduces the project and links to the documentation. |
| `setup.sh` | Creates local environment configuration. |
| `scripts/after-first-db-start.sh` | Runs database setup tasks after the first database start. |
| `scripts/backup-all.sh` | Backs up all project-created users. |
| `scripts/backup-user.sh` | Backs up one user. |
| `scripts/clear-schema.sh` | Removes objects from a schema. |
| `scripts/compress-space.sh` | Compresses a schema tablespace. |
| `scripts/create-self-signed-certificates.sh` | Creates local self-signed certificates. |
| `scripts/create-user.sh` | Creates a database user and optional APEX workspace. |
| `scripts/dev/reset.sh` | Resets the local development environment. |
| `scripts/disable-archive-logs.sh` | Disables archive logging for local development. |
| `scripts/disable-password-expiration.sh` | Disables APEX workspace password expiration. |
| `scripts/drop-user.sh` | Drops a database user and related local resources. |
| `scripts/fix-ws-group-ids.sh` | Updates APEX workspace exports before import. |
| `scripts/import-all.sh` | Imports all files from the import backup folder. |
| `scripts/import-backup.sh` | Imports one backup. |
| `scripts/import-datapump.sh` | Imports a Data Pump dump. |
| `scripts/install-dbms-cloud.sh` | Installs DBMS Cloud support. |
| `scripts/shrink-space.sh` | Reclaims unused database space. |
| `scripts/sql/drop_all.sql` | Drops objects from the current schema. |
| `scripts/sql/drop_apex_apps.sql` | Drops APEX applications. |
| `scripts/sql/drop_dp_tables.sql` | Drops Data Pump tables. |
| `scripts/start.sh` | Starts the local environment. |
| `scripts/stop.sh` | Stops the local environment. |
| `scripts/sync-backups-folder.sh` | Synchronizes backup folders. |
| `scripts/test-app-install.sh` | Tests an APEX application install. |
| `scripts/test-script-install.sh` | Tests a SQL script install. |
| `scripts/unexpire-accounts.sh` | Unlocks expired APEX accounts. |
| `scripts/upgrade-apex.sh` | Upgrades APEX in the local environment. |
| `scripts/used-space.sh` | Shows database space usage. |
| `scripts/util/create-datapump-directory.sh` | Creates a Data Pump directory. |
| `scripts/util/drop-sqlcl-connection.sh` | Removes a SQLcl connection. |
| `scripts/util/generate_password.sh` | Generates a password. |
| `scripts/util/get_ws_settings.sh` | Reads workspace settings. |
| `scripts/util/load_env.sh` | Loads environment variables. |
| `scripts/util/read_user_names.sh` | Reads user names from configuration. |
| `scripts/util/save-sqlcl-connection.sh` | Saves a SQLcl connection. |
| `scripts/util/user-exists-in-db.sh` | Checks whether a user exists in the database. |
| `scripts/util/user_in_env.sh` | Checks whether a user is listed in `.env`. |

## Contributing

Issues and pull requests are welcome. Improvements to the Bash scripts and documentation are especially helpful.

## Special Thanks

- The [contributors](https://github.com/United-Codes/uc-local-apex-dev/graphs/contributors).
- Connor McDonald for his blog post about [using Oracle Database Free disk space efficiently](https://connor-mcdonald.com/2023/12/18/the-ultimate-database-free-edition/).
- Tim Hall for the [`drop_all.sql`](https://oracle-base.com/dba/script?category=miscellaneous&file=drop_all.sql) script.
- Philipp Salvisberg for guidance on [using the PL/SQL debugger](https://gist.github.com/PhilippSalvisberg/2f2853bc7a95fa86d9de9c0deab10602).
- Scott Spendolini for his blog post about [adding self-signed certificates to ORDS](https://spendolini.blog/adding-ssl-to-your-ords-container).
- Matt Mulvaney for his blog post about [unexpiring ORDS accounts](https://mattmulvaney.hashnode.dev/unexpiring-the-ordspublicuser-user-for-apex).
- The Oracle Database team for providing an ARM image for Oracle Database.
- The ORDS team for providing an ARM image for ORDS.
