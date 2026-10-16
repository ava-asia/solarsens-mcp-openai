# SolarSENS plugin for ChatGPT

SolarSENS is the solar monitoring platform of AVA. This repository holds the
plugin package that AVA submits to the ChatGPT plugin directory. It gives
ChatGPT read-only access to the solar Plants that your SolarSENS account can
see, and five Skills that guide common checks.

## What the package contains

- `plugin.json`: the manifest, with the OpenAI listing fields under
  `extensions["com.openai"]`, the review test cases, and the release notes.
- `mcp.json`: one remote MCP server, `https://mcp.solarsens.co/mcp`, over
  Streamable HTTP with OAuth and dynamic client registration.
- `skills/`: five Skills. Plant performance review, string fault review, daily
  portfolio check, alarm triage, and missing value check.
- `assets/solarsens.png`: the logo.

There is no local code, hook, or script in this package.

## What the plugin does

- Signs you in with OAuth 2.1 (authorization code with PKCE) through the
  SolarSENS MCP login. The plugin never sees or stores your SolarSENS password.
- Reads only the Plants of the signed-in account. Every tool is read-only. The
  plugin cannot control equipment, acknowledge alarms, change configuration,
  or create work orders.
- Sends your requests and the returned monitoring data between ChatGPT and
  `mcp.solarsens.co` only.

See the [privacy policy](https://docs.solarsens.co/plugin/privacy/), the
[terms](https://docs.solarsens.co/plugin/terms/), and
[support](https://docs.solarsens.co/plugin/support/). The tool reference is at
<https://ai.solarsens.co/>.

## Getting access

A SolarSENS account linked for MCP sign-in is required. Ask your AVA contact
or <support@solarsens.co>.

## Maintenance

This repository is a mirror of the package that the SolarSENS MCP source
project builds with `pnpm plugin:build` and uploads as a zip. The source
project writes every file here except `README.md`, `LICENSE`, and
`.gitignore`. Do not edit the package files by hand; the next release
overwrites them.
