# "Mleap"

This project was bootstraped with the [create-python-api template](https://github.com/sequel-ae/gather-system-architecture/tree/main/software-templates/create-python-api)

# ML Engineering Applications Platform : thought process

## Overview

Welcome to the ML Engineering Applications Platform! This repository serves as a central hub for various self-serve packages designed to support data scientists from different domains in building and deploying machine learning models. The platform aims to streamline the machine learning engineering process, providing easy-to-use tools, utilities, and workflows.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Setting up Python Environment locally](#setting-up-python-environment-locally)
  - [Using pyenv](#using-pyenv)
- [Add the GCP Artifact Registry Repository name as a secret to the Github repository](#add-the-gcp-artifact-registry-repository-name-as-a-secret-to-the-github-repository)
- [Package Publishing](#package-publishing)
- [How to install this package](#how-to-install-this-package)
- [Pre-commit hooks](#pre-commit-hooks)
- [Running tests locally](#running-tests-locally)
- [Package List](#package-list)
  - [datazen ( renamed as mleap )](#datazen--renamed-as-mleap-)
  - [Package 2](#package-2)
  - [Package 3](#package-3)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The ML Engineering Applications Platform is a collaborative effort to provide data scientists with a set of powerful tools and frameworks to expedite the development and deployment of machine learning models. Our platform is designed with flexibility and extensibility in mind, making it suitable for various domains and machine learning use cases.

## Features

- **Modularity**: Each package is designed to address specific ML engineering tasks, promoting modularity and easy integration into existing workflows.
- **Documentation**: Comprehensive documentation is provided for each package, enabling users to understand and utilize the functionalities effectively.
- **Continuous Integration**: We employ continuous integration and testing pipelines to ensure the reliability and stability of the packages.
- **Collaborative Development**: We welcome contributions from the community, making it a collaborative platform to grow and improve over time.
- **Support for Diverse Domains**: Our packages are built with domain-agnosticism in mind, catering to data scientists with different backgrounds and projects.

## Setting up Python Environment locally

### Using pyenv

0) Install pyenv. See also: https://realpython.com/intro-to-pyenv/

1) Install python 3.8.13

```pyenv install -v 3.8.13```

2) Create a virtual environment named `"Mleap"`

```pyenv virtualenv 3.8.13 "Mleap"```

3) Activate the environment

```pyenv local "Mleap"```

4) Upgrade pip
`pip install --upgrade pip`

5) Install packages using pip
`pip install -r requirements.txt`

## Add the GCP Artifact Registry Repository name as a secret to the Github repository
Follow the steps [here](https://docs.github.com/en/actions/security-guides/encrypted-secrets) to add the GCP Artifact Registry Repository name as a secret to the Github repository.  The secret name should be `GCP_REPOSITORY_ARTIFACT_REGISTRY`.
The value of the secret should be the name of the artifact in the GCP Artifact Registry Repository.
If you need to create the artifact you can create it by following the steps [here](https://cloud.google.com/artifact-registry/docs/repositories/create-repos) setting the project to be a python project and the region as `us-central1`.

## Package Publishing
In order to update the artifact based on current github main you will need to run a github release and incrementing the version of `__version__.py`.

You can follow the industry standards for versioning found [here](https://py-pkgs.org/07-releasing-versioning.html) and the steps for starting a Github release [here](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository).
Create a new tag for the version release that is `v$PackageVersion`. For example if you were making a release
for version 0.0.1 the tag would be `v0.0.1`.  The release name should be the same as the tag name.

## How to install this package
This package is currently available on Google artifact registry. To install the Google artifact registry, run the following in your terminal:
1) `pip install keyring`
2) `pip install keyrings.google-artifactregistry-auth`
3) Create Application Default Credentials by running the following in the terminal:
    - `gcloud auth application-default login`
    - `gcloud auth login`
4) Set the GCP default project id by running the following in the terminal
    - `gcloud auth application-default set-quota-project ai-ml-00`
5) Install the package using the following command replacing $GCP_ARTIFACT_NAME with the name of the artifact in the GCP Artifact Registry Repository name and package_name with the name of the package.
    - `pip install --extra-index-url https://us-central1-python.pkg.dev/ai-ml-00/$GCP_ARTIFACT_NAME/simple/ package_name`

To add the package to your requirements.txt file, add the following to your requirements.txt file
Replacing $GCP_ARTIFACT_NAME with the name of the artifact in the GCP Artifact Registry Repository name and package_name with the name of the package.
```
--extra-index-url https://us-central1-python.pkg.dev/ai-ml-00/mleap/simple/ mleap_transporter
```

## How to use the package in other projects

After installing the package (see above), you can import the package in your project using the following code as an example:
``
from mleap_transporter import experiment, versioning
``

## Pre-commit hooks
See also documentation [here](https://pre-commit.com)
1) Assuming the pre-commit package is installed, install the git hook scripts
`pre-commit install`

## Running tests locally

  ```pytest -vv```

Running this command from the root of the project should find and execute the tests.  Use `-vv` to show detail about which tests are running and the completion state of each.  These should run quickly.

## Package List

Here's a list of packages available in this repository:

### datazen ( renamed as transporter )

_Description of package 1, its functionalities, and intended use._

### Package 2

_Description of package 2, its functionalities, and intended use._

### Package 3

_Description of package 3, its functionalities, and intended use._

## Contributing

We welcome contributions to the ML Engineering Applications Platform. If you have ideas for new packages, improvements to existing ones, or general suggestions, feel free to open an issue or submit a pull request. Please ensure you follow our guidelines for contributing.

## License

The ML Engineering Applications Platform is open-source and licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute the code as per the terms of the license.

---

We hope this platform enhances your machine learning journey and empowers you to build innovative and powerful models. Happy coding and data science!
