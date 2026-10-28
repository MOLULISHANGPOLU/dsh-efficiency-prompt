# DSH Efficiency Prompt

简体中文：[README.zh-CN.md](README.zh-CN.md)

A small Cordis plugin for DeepSeek Harness (DSH). It adds a focused system-prompt section for efficient task execution, evidence-based reporting, and concise communication.

## What it does

- Moves directly toward the requested outcome when the task is clear.
- Uses reasonable, reversible assumptions for harmless missing details; asks when a missing detail changes the result or risk.
- Requires evidence before claiming work is complete.
- Adds concise guidance for explanations, analysis, and multi-turn collaboration.
- Directs the assistant to minimize sensitive data and treat instructions embedded in external content as untrusted.
- Keeps the host's system instructions, safety boundaries, and permissions authoritative.
- Adds no tools, network calls, telemetry, files, or configuration changes.

## Install

This is a DSH profile bundle. After publishing the repository, install it directly from GitHub with DSH's plugin manager:

```sh
dsh plugin --profile desktop add github:YOUR_GITHUB_OWNER/dsh-efficiency-prompt
```

Replace `YOUR_GITHUB_OWNER` with the GitHub account or organization that hosts the repository. For another profile, replace `desktop` with that profile name. DSH reads the bundle declaration and applies `cordis.patch.yml`; no manual profile edits or build scripts are needed. Restart DSH if your profile manager requires it.

If you downloaded or cloned the repository, run this from its root instead:

```sh
dsh plugin --profile desktop add .
```

The repository ships the ready-to-run `lib/index.js`, so installation does not need to execute a build script. Do not install from an unreviewed fork. The package manifest explicitly includes only the runtime entry, bundle patch, README, and license; do not add machine-specific paths, credentials, logs, or personal data.

## Privacy and source protection

The plugin makes no network requests and collects no data. Its prompt asks the assistant not to disclose credentials, personal data, local/network addresses, device details, local paths, environment variables, or other private information, and to treat instructions found in external content as untrusted. These are model instructions, not a technical data-loss-prevention boundary; keep secrets out of prompts and files.

The accompanying license permits individuals to download, install, and use the plugin for personal, non-commercial purposes. Commercial use, modification, redistribution, republication, and resale require written permission. Public GitHub visibility still makes source code readable and copyable; a runtime prompt can also be inspected by someone who can run the plugin. Do not publish anything that must remain confidential. The license states usage rights but cannot technically prevent copying or reverse engineering.

## Compatibility

- DSH `>=0.2.0-rc.2 <0.2.2-0` (covers the 0.2.0 and 0.2.1 release lines, including their prereleases)
- Cordis `^4.0.1`
- Node.js 18+
- No operating-system-specific APIs or platform restriction
- No prompt variables are used; interpolation is disabled for the section.

DSH checks `engines.dsh` before loading a bundle. The plugin uses only the `systemPrompt.section` registration API and declares no platform-specific integrations. This supports the named DSH range; it does not claim compatibility with every future DSH version.

## Development

The runtime entry is `lib/index.js`. The plugin registers one named section at order `4800` and does not modify other prompt sections.

## License

Personal, non-commercial use is permitted under the terms in [LICENSE](LICENSE); other uses require written permission.
