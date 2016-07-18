# [Cloud.Gov](https://cloud.gov/) Application SSP Example
A generic SSP setup example for Cloud.Gov-based applications.

## Background
Because [Cloud.Gov](https://cloud.gov/) was designed to be compliant with U.S. Government security standards [(see NIST-800-53)](https://web.nvd.nist.gov/view/800-53/home), many of the infrastructure and platform security requirements have been pre-implemented for all applications deployed on [Cloud.Gov](https://cloud.gov/).

Nevertheless, U.S. Government security standards necessitate that every public-facing application (even those deployed on [Cloud.Gov](https://cloud.gov/)) implement additional security measures and document the compliance requirements of the entire application infrastructure.

In order to leverage [Cloud.Gov's](https://cloud.gov/) existing compliance documentation, 18F is starting to construct its documentation using the [Compliance Masonry CLI](https://github.com/opencontrol/compliance-masonry).

The [Compliance Masonry CLI](https://github.com/opencontrol/compliance-masonry) allows users to build documentation like they build code. This includes the ability to set [Cloud.Gov's Compliance Documentation](https://compliance.cloud.gov/) as a dependency for their application's documentation in the same way a developer set dependencies in package.json, Gemfile, or requirements.txt files.

The schema or language used to create compliance documentation for compliance masonry is [the opencontrol schema](https://github.com/opencontrol/schemas).

## [opencontrol.yaml](https://github.com/opencontrol/compliance-masonry#creating-an-opencontrol-project)
The [opencontrol.yaml](https://github.com/opencontrol/compliance-masonry#creating-an-opencontrol-project) defines an application's documentation configuration settings, in the same vein as a `manifest.yaml` defines the deployment configuration settings for an application built on [Cloud.Gov](https://cloud.gov/).

See this repository's [`opencontrol.yaml`](opencontrol.yaml) for a minimal example for an application built on top of cloud.gov.

## Setup
0. Clone this repository.
0. Follow the [Compliance Masonry Quick Start](https://github.com/opencontrol/compliance-masonry#quick-start).
