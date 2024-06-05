# Deploy PyPI to GitHub Pages

This GitHub Action publishes a static PyPI repository to GitHub Pages.

## Table of Contents
1. [Action Summary](#action-summary)
2. [Pre-requisites](#pre-requisites)
3. [Basic Use](#basic-use)
4. [Inputs](#inputs)
5. [Permissions](#permissions)
6. [Contributing](#contributing)
7. [License](#license)
8. [Provided by Bitovi](#provided-by-bitovi)
9. [We want to hear from you](#we-want-to-hear-from-you)

## Action Summary

This action performs the following steps to publish a static PyPI repository to GitHub Pages:
1. Check out the repository (optional).
2. Upload the PyPI package as a GitHub Pages artifact.
3. Deploy the package to GitHub Pages.

If you would like to deploy other types of applications, check out our other actions:
| Action | Purpose |
| ------ | ------- |
| [Deploy Docker to EC2](https://github.com/marketplace/actions/deploy-docker-to-aws-ec2) | Deploys a repo with a Dockerized application to a virtual machine (EC2) on AWS |
| [Deploy Storybook to GitHub Pages](https://github.com/marketplace/actions/deploy-storybook-to-github-pages) | Builds and deploys a Storybook application to GitHub Pages. |
| [Deploy static site to AWS (S3/CDN/R53)](https://github.com/marketplace/actions/deploy-static-site-to-aws-s3-cdn-r53) | Hosts a static site in AWS S3 with CloudFront |
<br/>

**And more!**, check our [list of actions in the GitHub marketplace](https://github.com/marketplace?category=&type=actions&verification=&query=bitovi)

## Need help or have questions?

This project is supported by [Bitovi, A DevOps consultancy](https://www.bitovi.com/services/devops-consulting).

You can **get help or ask questions** on our:

- [Discord Community](https://discord.gg/zAHn4JBVcX)

Or, you can hire us for training, consulting, or development. [Set up a free consultation](https://www.bitovi.com/services/devops-consulting).

## Pre-requisites
- A GitHub repository with a PyPI directory.  The directory should be a set of HTML files that represent the Package Index. For more information about the directory structure, check out [PEP503](https://peps.python.org/pep-0503/#specification).

> **Note:** Check out Bitovi's [Publish to GitHub PyPI](https://github.com/bitovi/github-actions-publish-github-pypi) and [Publish to GitHub PyPI handler](https://github.com/bitovi/github-actions-publish-github-pypi-handler) actions to set up a GitHub-hosted managed PyPI ecosystem.

## Basic Use

For basic usage, create `.github/workflows/deploy-github-pages.yaml` with the following to build and publish the package:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

permissions:
  pages: write
  id-token: write

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - name: Publish PyPI and Deploy to GitHub Pages
        uses: bitovi/github-actions-publish-github-pypi@v0.1.0
```

## Inputs

The following inputs can be used as `step.with` keys:

| Name        | Type    | Description                                                   |
|-------------|---------|---------------------------------------------------------------|
| `checkout`  | Boolean | (Optional) Whether to checkout the repository. Default is `true` |
| `pypi-path` | String  | (Optional) Path to the PyPI package. Default is `pypi/`       |

## Permissions

Ensure the following permissions are added to your workflow file to deploy to GitHub Pages:
```yaml
permissions:
  pages: write      # to deploy to Pages
  id-token: write   # to verify the deployment originates from an appropriate source
```

## Contributing

We would love for you to contribute to this action. [Issues](https://github.com/bitovi/github-actions-publish-github-pypi/issues/new/choose) and Pull Requests are welcome!

## License

The scripts and documentation in this project are released under the MIT License.

# Provided by Bitovi

[Bitovi](https://www.bitovi.com/) is a proud supporter of Open Source software.

# We want to hear from you.

Come chat with us about open source in our Bitovi community [Discord](https://discord.gg/J7ejFsZnJ4Z)!