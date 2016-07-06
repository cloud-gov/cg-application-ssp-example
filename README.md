# [Cloud.Gov](https://cloud.gov/) Application SSP Example
A generic SSP setup example for Cloud.Gov-based applications.

## Background
Because [Cloud.Gov](https://cloud.gov/) was designed to be compliant with U.S. Government security standards [(see NIST-800-53)](https://web.nvd.nist.gov/view/800-53/home), many of the infrastructure and platform security requirements have been pre-implemented for all applications deployed on [Cloud.Gov](https://cloud.gov/).

Nevertheless, U.S. Government security standards necessitate that every public-facing application (even those deployed on [Cloud.Gov](https://cloud.gov/)) implement additional security measures and document the compliance requirements of the entire application infrastructure.

In order to leverage [Cloud.Gov's](https://cloud.gov/) existing compliance documentation, 18F is starting to construct its documentation using the [Compliance Masonry CLI](https://github.com/opencontrol/compliance-masonry).

The [Compliance Masonry CLI](https://github.com/opencontrol/compliance-masonry) allows users to build documentation like they build code. This includes the ability to set [Cloud.Gov's Compliance Documentation](https://compliance.cloud.gov/) as a dependency for their application's documentation in the same way a developer set dependencies in package.json, Gemfile, or requirements.txt files.

The schema or language used to create compliance documentation for compliance masonry is [the opencontrol schema](https://github.com/opencontrol/schemas).

## Main Concepts
### [Components](https://github.com/opencontrol/schemas#component-yaml)
Components represent individual parts of an application that deal with specific security requirements. For example, in the [AWS compliance documentation](https://github.com/opencontrol/aws-compliance) the [EC2](https://github.com/opencontrol/aws-compliance/blob/master/IAM/component.yaml) component deals with access control and identity management security requirements. In the [Cloud Foundry compliance documentation](https://github.com/opencontrol/cf-compliance), the [UAA](https://github.com/opencontrol/cf-compliance/blob/master/UAA/component.yaml) the [Cloud Controller](https://github.com/opencontrol/cf-compliance/tree/master/CloudController) components deal with those requirements. In a straightforward Django-based application, for example, Django would be the component that deals with access control and identity management. As a developer building an SSP you most likely only deal with the component documentation.

### [Standards](https://github.com/opencontrol/schemas#standards-documentation)
A standard is a list composed of individual security requirements called controls. The U.S. Government's main security standard is [NIST-800-53](https://web.nvd.nist.gov/view/800-53/home).

### [Certifications](https://github.com/opencontrol/schemas#certifications)
Since standards can have thousands of security requirements (aka controls), agencies like the GSA or organizations such as [FedRAMP](https://www.fedramp.gov) have curated a list of controls they require in order grant an IT system Authority to Operate (ATO). The GSA, for example, developed a certification called [the Lightweight ATO (LATO)](https://gsablogs.gsa.gov/innovation/2014/12/10/it-security-security-in-an-agile-development-cloud-world-by-kurt-garbars/), which uses only 24 controls.

### [opencontrol.yaml](https://github.com/opencontrol/compliance-masonry#creating-an-opencontrol-project)
The [opencontrol.yaml](https://github.com/opencontrol/compliance-masonry#creating-an-opencontrol-project) defines an application's documentation configuration settings in the same vein as a manifest.yaml defines the deployment configuration settings for an application built on [Cloud.Gov](https://cloud.gov/).

Below is an example of a opencontrol.yaml file with descriptions of the fields:
```yaml
schema_version: "1.0.0" # 1.0.0 is the current opencontrol.yaml schema version
name: Project Name # Name of the project
metadata:
  description: "A description of the system"
  maintainers:
    - maintainer_email@email.com
components: # A list of paths to components written in the opencontrol format for more information view: https://github.com/opencontrol/schemas
  - ./component-1
certifications: # An optional list of certifications for more information visit: https://github.com/opencontrol/schemas
  - ./cert-1.yaml
standards: # An optional list of standards for more information visit: https://github.com/opencontrol/schemas
  - ./standard-1.yaml
dependencies:
  certifications: # An optional list of certifications stored remotely
    - url: https://github.com/18F/GSA-Certifications
      revision: master
  systems:  # An optional list of repos that contain an opencontrol.yaml stored remotely
    - url: https://github.com/18F/cg-compliance
      revision: master
  standards:   # An optional list of remote repos containing standards info that contain an opencontrol.yaml
    - url: https://github.com/opencontrol/NIST-800-53-Standards
      revision: master
```

## Setup
0. Clone this repository.
0. Follow the [Compliance Masonry Quick Start](https://github.com/opencontrol/compliance-masonry#quick-start).
