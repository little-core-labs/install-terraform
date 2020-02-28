# install-terraform
Install Terraform to a Github Actions job environment.

<a href="https://github.com/little-core-labs/install-terraform"><img alt="GitHub Actions status" src="https://github.com/little-core-labs/install-terraform/workflows/Tests/badge.svg"></a>


## Usage

### Pre-requisites
Create a workflow `.yml` file in your repositories `.github/workflows` directory. An [example workflow](#example-workflow) is available below. For more information, reference the GitHub Help Documentation for [Creating a workflow file](https://help.github.com/en/articles/configuring-a-workflow#creating-a-workflow-file).


### Inputs

- `version`: The version of terraform to install. Default: 0.12.21

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
      uses: little-core-labs/install-terraform@v1
    - name: Terraform apply
      run: |
        terraform init
        terraform plan
        terraform apply -auto-approve
```

## License
The scripts and documentation in this project are released under the [MIT License](LICENSE)
