---
layout: default
title: linting terraform
description: "keeping terraform nice and neat"
order: 14
---

<p>Managing infrastructure can be an overtly daunting task made no less confusing by having a big spaghetti codebase. In order to maintain a high standard of code you can implement a number of easy checks in your deployment pipeline.</p>

<h2>terraform fmt</h2>

```yaml
jobs:
  terraform_fmt:
    name: "Terraform fmt"
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Setup Terraform
        uses: hashicorp/setup-terraform@v2
        with:
          terraform_version: ...
          cli_config_credentials_token: ...

      - name: Terraform fmt
        id: fmt
        run: terraform fmt -check -recursive
```

<a href="https://developer.hashicorp.com/terraform/cli/commands/fmt"> documentation</a>

<h2>tflint</h2>

```yaml
  terraform_lint:
    name: "Terraform Lint"
    needs: [terraform_fmt]
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Setup tflint
        run: |
          curl -s https://raw.githubusercontent.com/terraform-linters/tflint/master/install_linux.sh | bash
          tflint --init
      - name: Run tflint
        run: |
          tflint --recursive --config "$(pwd)/.tflint.hcl"
```

<a href="https://github.com/terraform-linters/tflint">documentation</a>
<p>An example config for tflint using <span>.tflint.hcl</span></p>

```yaml
plugin "aws" {
    enabled = true
    version = "0.26.0"
    source  = "github.com/terraform-linters/tflint-ruleset-aws"
}

rule "terraform_naming_convention" {
  enabled = true
}
```
<p></p>


