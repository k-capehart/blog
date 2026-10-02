---
title: "Open Source Contributions"
date: 2024-08-23T11:18:58-04:00
weight: 25
summary: "Contributions to open source projects"
descriptions: "Contributions to open source projects"
tags: []
badges:
  - "Open Source"
links:
  - icon: fab fa-github
    url: https://github.com/k-capehart
showReadMore: true
draft: false
---


A collection of contributions I have made to open source projects.

## Salesforce DX
Official Salesforce open source projects include [salesforcecli](https://github.com/salesforcecli), [oclif](https://github.com/oclif), [salesforcedx-apex](https://github.com/forcedotcom/salesforcedx-apex), and [salesforcedx-vscode](https://github.com/forcedotcom/salesforcedx-vscode)

- [PR#6599](https://github.com/forcedotcom/salesforcedx-vscode/pull/6599) / [PR#6636](https://github.com/forcedotcom/salesforcedx-vscode/pull/6636) - Add `test-run-concise` option to Visual Studio code for concise apex results
- [PR#504](https://github.com/salesforcecli/plugin-apex/pull/504) / [PR#553](https://github.com/salesforcecli/plugin-apex/pull/553) - Add `concise` flag to `sf apex run test` to suppress successful test results in terminal output
- [PR#377](https://github.com/forcedotcom/salesforcedx-apex/pull/377) / [PR#383](https://github.com/forcedotcom/salesforcedx-apex/pull/383) - Reformat terminal output for apex test results
- [PR#873](https://github.com/salesforcecli/plugin-deploy-retrieve/pull/873) - Add `concise` flag to `sf project deploy preview` to suppress ignored files from displaying in terminal output
- [PR#886](https://github.com/salesforcecli/plugin-auth/pull/886) - Add `sfdx-url-stdin` flag to allow users to include their SFDX Authorization URL to be piped into the `sf org login sfdx-url` command as standard input
- [PR#894](https://github.com/oclif/core/pull/894) - Allow standard input to be read as a value for flags

## SFDX-Hardis

An open source plugin for the Salesforce CLI and VS Code extension that offers a variety of features.

- [PR#288](https://github.com/hardisgroupcom/vscode-sfdx-hardis/pull/288) - Fix a bug related to setting custom themes in VS Code
- [PR#903](https://github.com/hardisgroupcom/sfdx-hardis/pull/903) - Fix an issue where the last modified date was calculated based off of metadata files rather than the class file

## Lightning Flow Scanner

A community created plugin that scans Flows in Salesforce for deviations from best practices.
- [PR#96](https://github.com/Lightning-Flow-Scanner/lightning-flow-scanner-sfdx/pull/96) - Enable automated dependency updates with Dependabot
- [PR#94](https://github.com/Lightning-Flow-Scanner/lightning-flow-scanner-sfdx/pull/94) - Enable automated testing via GitHub Actions
- [PR#83](https://github.com/Lightning-Flow-Scanner/lightning-flow-scanner-core/pull/83) - Implement new rule to detect flows that are inactive
