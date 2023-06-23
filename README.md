# Platform Security GitHub Workflow

This project aims to provide Red Hat ConsoleDot Teams with a way to scan the containers they create in a convenient, automated, and reliable manner within their GitHub repository. The `Platform Security Github Workflow` lets teams get security feedback as they open Pull Requests and fix any vulnerability before committing the code to a repository.

The `Platform Security Workflow` uses the free and open-source security tools Anchore's [Syft](https://github.com/anchore/syft/) and [Grype](https://github.com/anchore/grype/). 

* `Syft` generates a Software Bill of Materials (SBOM) from container images and filesystems.

* `Grype` conducts vulnerability scanning for container images and filesystems. Additionally, it uses [RedHat Linux Security Data](https://access.redhat.com/hydra/rest/securitydata/), making the scanning and reporting of vulnerabilities incredibly accurate regarding how we build our applications.


## Getting Started

Getting started with the `Platform Security Github Workflow` is as easy as copying the `security-workflow-template.yml` file from this repository and adding it to your GitHub repository's `.github/workflows` directory. Doing so will enable security scanning (via our reusable GitHub workflow) anytime a Pull-Request is opened or merged.

After the workflow has run, you can download artifacts of the results from the associated `workflow run`. The artifacts will contain the following files:

* grype-vuln-results-full.txt
* grype-vuln-results-fixable.txt
* syft-sbom-results.txt

Additionally, if the container image built and scanned contains any fixable vulnerabilities of `High` or `Critical` severity, the `Grype-Vulnerability-Scan` portion of the workflow will be flagged as a failure and let you know the reason. 

**Please Note:** You may have to enable the following in the `actions/general` settings:
* Fork pull request workflows
   * Run workflows from fork pull requests
   * Require approval for fork pull request workflows.


## What about updates?
The `security-workflow-template.yml` file is pre-configured to use the reusable GitHub workflow in the `main/master` branch of this repository, so any updates to the scanners or functionality done by the Platform-Security Team will be automatically inherited. 
