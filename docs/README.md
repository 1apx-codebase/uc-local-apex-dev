# UC Local APEX Dev Documentation

This folder contains the documentation site for UC Local APEX Dev. The site uses Astro Starlight.

## Contents

- `src/content/docs/`: Documentation pages.
- `src/assets/`: Images and other source assets.
- `public/`: Static files such as the favicon.
- `astro.config.mjs`: Site, sidebar, and plugin configuration.

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
