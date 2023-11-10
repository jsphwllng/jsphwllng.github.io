---
layout: default
title: fully automated luxury gay space github actions
description: "writing reusable chunks of CI/CD for profit and a good time"
order: 15
---
<p>It's time to talk about the delight of every platform engineer and the nightmare of every developer - CI/CD pipelines. With the emergence of Github Actions as one of the most prevalent tools for pipelines it is worth developing reusable actions for these pipelines.</p>
<p>Github actions, if public, are reusable by anyone else on Github. If private and within an organisation they can be reused within that organisation. This makes it incredibly easy to develop reusable chunks of code across a team.</p>
<p>For example, as I spoke about in <a href="/blog/linting_terraform">linting terraform</a> these steps can be applicable across many repositories. Having a local repository with the following code: </p>
<code>
# example-repository/.github/workflows/pretty_terraform.yml
  
name: "Check if terraform is pretty"  

on:
  workflow_call:
  inputs:
    tf_ver:
      type: string
      default: 1.3.0
    creds_token:
      type: string
      required:true

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
          terraform_version:
            {% raw %}${{ inputs.tf_ver }}}{% endraw %}
          cli_config_credentials_token: 
            {% raw %}${{ inputs.creds_token }}}{% endraw %}

      - name: Terraform fmt
        id: fmt
        run: terraform fmt -check -recursive
</code>

<p>Means that it can be referenced in the following way in an entirely different repository:</p>
<code>
# example-infra-repo/.github/workflows/pretty.yml
name: "lint terraform"
on: push

jobs:
  lint:
    name: "Initial lint of terraform"
    uses: example-repository/.github/workflows/pretty_terraform.yml@main
    with:
      creds_token: "blahblah"
</code>
<p>The benefits here really reflect the <a href="https://en.wikipedia.org/wiki/Don%27t_repeat_yourself">DRY principle</a> meaning that multiple deployments can be modified at once rather than having to be done individually. Additionally the end of the <i>uses</i> key has a reference to the branch (in this case main) however this can be development branches, released versions, anything.</p>
<p>These actions can also be baked into Github repo configurations meaning that each repository will have the same checks run on them. This can be useful for secrets checking, code quality or general security concerns.</p>
<p>After working with Jenkins, Travis CI and ArgoCD I am thoroughly convinced that Github actions is the way to go.</p>

