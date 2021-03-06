# install-terraform
Install Terraform to a Github Actions job environment.

<a href="https://github.com/little-core-labs/install-terraform"><img alt="GitHub Actions status" src="https://github.com/little-core-labs/install-terraform/workflows/Tests/badge.svg"></a>


## Usage

### Pre-requisites
Create a workflow `.yml` file in your repositories `.github/workflows` directory. An [example workflow](#example-workflow) is available below. For more information, reference the GitHub Help Documentation for [Creating a workflow file](https://help.github.com/en/articles/configuring-a-workflow#creating-a-workflow-file).


### Inputs

- `version`: The version of terraform to install. Required.

### Outputs

None.

### Example workflow

```yaml
name: Example installing Terraform

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [12.x]

    steps:
    - uses: actions/checkout@v1
    - name: Install Terraform
      uses: little-core-labs/install-terraform@v2.0.0
      with:
          version: 0.13.4
    - name: Terraform apply
      run: |
        terraform init
        terraform plan
        terraform apply -auto-approve
```

## FAQ

### Can you offer a major version tag/branch alias?  I want automatic updates!

Nope!  This was always weird/bad pattern of github actions.  Luckily github offers a solution for this.  Create a `.github/dependabot.yml` with, at a minimum, the following config:

```yaml
# Basic dependabot.yml file with
# minimum configuration for two package managers

version: 2
updates:
  # Enable updates to github actions
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "daily"

```


## License
The scripts and documentation in this project are released under the [MIT License](LICENSE)
