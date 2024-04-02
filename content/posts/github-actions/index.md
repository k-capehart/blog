+++
title = 'Automate your Salesforce Deployments with GitHub Actions'
date = 2024-04-02T10:38:35-04:00
draft = true
categories = ['salesforce', 'dev-ops']
keywords = ['salesforce', 'sf', 'sfdc', 'dev-ops', 'dev ops', 'github actions', 'automating salesforce release', 'yaml', 'gh actions', 'salesforce pipeline', 'sf release', 'salesforce cli', 'sfdx', 'ci/cd', 'sf project deploy', 'sfdx authorization url', 'sf org login', 'sf org login sfdx-url', 'securely login salesforce', 'sf org display --verbose', 'devops center', 'change sets', 'ant migration tool retirement', 'ant migration end of life']
+++

Streamline your release pipeline in just a few steps.

## Using the right tools
There are many tutorials that cover automating Salesforce deployments. This article's intention is to cover a few gaps and ensure release managers are using the best available tools.
- Use newer `sf-cli` over the deprecated `sfdx-cli` ([announcement](https://developer.salesforce.com/blogs/2023/07/salesforce-cli-sf-v2-is-here))
- Utilize new `sfdx-url-stdin` authorization method from [sf-cli Release 2.24.4](https://github.com/forcedotcom/cli/blob/main/releasenotes/README.md#2244-jan-17-2024) (implemented by yours truly)

## CI/CD in Salesforce
CI/CD stands for [continuous integration and continuous delivery/deployment](https://www.redhat.com/en/topics/devops/what-is-ci-cd) and describes the process by which software development teams quickly develop and deploy applications.

In the world of Salesforce, this means being able to automate deployments from scratch orgs (and sandboxes) all the way to production. This involves keeping track of projects in a version control repository like GitHub, so that changes can be identified between releases. [Source-driven development in Salesforce](https://trailhead.salesforce.com/content/learn/modules/sfdx_dev_model/sfdx_dev_model_sdd) means the source of truth for metadata is in version control rather than in an org. This enables development teams to seamlessly integrate changes and customization because everyone is working off of the same version.

### Change Sets
The classic way to perform deployments in Salesforce is through [Change Sets](https://help.salesforce.com/s/articleView?id=sf.changesets.htm&type=5). However, these are not recommended for a number of reasons.
- No automation - developers have to manually choose components to deploy
- Limited auditing capabilities - no way to track changes between deployments
- Incomplete metadata support - [not all metadata types](https://help.salesforce.com/s/articleView?id=sf.changesets_about_components.htm&type=5) (like picklist values or sales processes) can be deployed

### Ant Migration Tool
The Ant Migration tool is another method often used, but [Salesforce announced its retirement](https://developer.salesforce.com/blogs/2024/01/moving-on-from-the-ant-migration-tool-to-sf-cli-v2?_ga=2.156343547.1799736251.1705831920-1945174671.1701548171) in 2024. As such, it's not recommended for new implementations.

### DevOps Center
The new and improved [DevOps Center](https://www.salesforce.com/products/devops-tools/) is the preferred method for deploying and is [recommended over change sets](https://trailhead.salesforce.com/content/learn/modules/devops-center-quick-look/say-hello-to-devops-center) in official trainings. It solves many of the issues facing Change Sets and can directly integrate with a source control repository. DevOps center is a great solution for many teams, but is intended for Admins not familiar with the `sf-cli`. It may not be needed if everyone on the team is already using git from the command line.


### SF CLI and GitHub Actions
The `sf-cli` is Salesforce's powerful new command line tool that supports executing SOQL queries, running apex tests, creating and deploying metadata, and more. Developers should already be familiar with it so the transition to GitHub Actions is simple. Workflows can be created to automatically run `sf-cli` commands when a specified action (like opening a pull request or creating a release) occurs in a GitHub repository. Developers no longer have to manually run commands, so Salesforce environments will always be in sync with source control, making it the sole source of truth.


## Creating a workflow using GitHub Actions

### What you need
There are a few prerequisites, all entirely free.
- Create a [GitHub account](https://github.com/join)
    - Read about [creating a GitHub repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories)
- Sign up for a [Salesforce Developer Edition org](https://developer.salesforce.com/signup)
- Download the [Salesforce Command Line Interface](https://developer.salesforce.com/tools/salesforcecli)
    - If you are using the old `sfdx-cli`, [upgrade to the new `sf-cli`](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_move_to_sf_v2.htm)
- Install the [Visual Studio Code with Salesforce Extension Pack](https://developer.salesforce.com/tools/vscode)
- Setup your [Salesforce Developer Environment in VS Code](https://trailhead.salesforce.com/content/learn/projects/quick-start-lightning-web-components/set-up-visual-studio-code)

### Step-by-step

### Demo

## Conclusion