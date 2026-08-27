# Tools

<p align="center">
    <a href="https://stackoverflow.com/questions/tagged/moryx">
        <img src="https://img.shields.io/badge/stackoverflow-ask-orange.svg" alt="Stackoverflow">
    </a>
</p>

## Overview

This repo contains GitHub Actions, Workflows and other tools that the MORYX team uses to maintain quality.

## Adding the workflow to MORYX-Repositories

The current standard workflow in MORYX-Repositories includes:

- Buildung the solution and package it
- Unit-Testing with coverage information collection
- Integration-Testing with coverage information collection
- Generating a coverage report via ReportGenerator
- Documentation
- Publishing built packages to Myget or Nuget

To add this workflow to your MORYX-Repository, follow these steps:

 1. Add the nuget-package "coverlet.collector" to your test-projects and also add a package-reference with version to *Directory.build.targets*.
 2. Make sure, you have the *.build*-directory with all its content.
 3. Add the needed secrets to your repository: AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, MYGET_TOKEN, NUGET_TOKEN.
 4. Add the *build-and-test-tool.yml* as *build-and-test.yml* to your repository to *.github/workflows/* in your repository.

For reference, the workflow is currently in use in the follwing repositories: [MORYX-Framework](https://github.com/PHOENIXCONTACT/MORYX-Framework).

## Contribute

If you have an idea to improve a template or can think of a new useful template, please make your changes based on one of the template branches and open a pull request. If you want to add a template, extend the branch list in one commit and the template definition in another. This way we can easily put your template into a separate branch. **Note:** All branches except *main* will be rebased regularly, to keep grafting them easy. To avoid losing previous merge request information, all branch merge requests are merged by rebase squashing.