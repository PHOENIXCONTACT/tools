# Tools

<p align="center">
    <a href="https://stackoverflow.com/questions/tagged/moryx">
        <img src="https://img.shields.io/badge/stackoverflow-ask-orange.svg" alt="Stackoverflow">
    </a>
    <a href="https://gitter.im/PHOENIXCONTACT/MORYX?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge">
        <img src="https://badges.gitter.im/PHOENIXCONTACT/MORYX.svg" alt="Gitter">
    </a>
</p>

## Overview
This repo contains GitHub Actions, Workflows and other tools that the MORYX team uses to maintain quality.
</br>
Currently including:

- GitHub reusable workflows: *.github/workflows/*
- Landing Page for the [MORYX-CodeCoverage-Website](https://d2g620u22bjjnb.cloudfront.net/): *src/CodeCoverage-Pages/*
- Action to sync Landing Page to AWS Server (in progress)

## Adding the workflow to MOYRX-Repositories

The current standard workflow in MORYX-Repositories includes:

- Buildung the solution and package it
- Unit-Testing with coverage information collection
- Integration-Testing with coverage information collection
- Generating a coverage report via ReportGenerator
- Syncing coverage html-pages to AWS-S3-Bucket
- Documentation
- Publishing built packages to Myget or Nuget

To add this workflow to your MORYX-Repository, follow these steps:

 1. Add the nuget-package "coverlet.collector" to your test-projects and also add a package-reference with version to *Directory.build.targets*.
 2. Make sure, you have the *.build*-directory with all its content.
 3. Add the needed secrets to your repository: AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, MYGET_TOKEN, NUGET_TOKEN.
 4. Add the *build-and-test-tool.yml* as *build-and-test.yml* to your repository to *.github/workflows/* in your repository.

For reference, the workflow is currently in use in the follwing repositories: [MORYX-Framework](https://github.com/PHOENIXCONTACT/MORYX-Framework) and [MORYX-Factory](https://github.com/PHOENIXCONTACT/MORYX-Factory).

### Adding the repository coverage results to the MORYX-CodeCoverage-Website

To add the information gathered in the workflow to be shown on the MORYX-CodeCoverage-Website in *src/CodeCoverage-Pages/*, please add the html-code and JavaScript according to the comments in the files, respectively.

## Contribute

If you have an idea to improve a template or can think of a new useful template, please make your changes based on one of the template branches and open a pull request. If you want to add a template, extend the branch list in one commit and the template definition in another. This way we can easily put your template into a separate branch. **Note:** All branches except *master* will be rebased regularly, to keep grafting them easy. To avoid losing previous merge request information, all branch merge requests are merged by rebase squashing.

### Github ref variables

The detailted documentation is [here](https://docs.github.com/de/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#github-context). However it was not always obvious what value was where.

- current branch: When building on a push to e.g. dev, the current branch is in `ref_name`. However in pull requests this refers to the pull-request id and you need `head_ref` instead