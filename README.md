# AWS EC2 - Configure Access (KeyPair)
GitHub Actions - Configure Access (KeyPair) - Access As A Service (AaaS)

![GitHub Actions - AWS EC2 Configure Access](https://github.com/emvaldes/configure-access/workflows/GitHub%20Actions%20-%20AWS%20EC2%20Configure%20Access/badge.svg)

**<span style="color:red">1</span>** -) Create a Public|Private GitHub Repository for your project

**<span style="color:red">2</span>** -) Inject your project into your GitHub Repository

**<span style="color:red">3</span>** -) Create the GitHub Secrets to store sensitive|private data

```console
PRIVATE_KEYPAIR_FILE:   Location for KeyPair File (e.g.: ~/.ssh/id_rsa)
PRIVATE_KEYPAIR_SECRET: Secret content (e.g.: *.PEM, id_rsa, etc.)
```
**<span style="color:red">4</span>** -) Create a GitHub Action - Pipeline to deploy your project: .github/workflows/main.yaml <br>
**Note**: This is just a prototype of how to use this GitHub Action (uses: emvaldes/configure-access@v1.0)

[Pipeline Deployment](https://github.com/emvaldes/configure-access/blob/master/.github/workflows/main.yaml)

```console
name: GitHub Actions - AWS EC2 Configure Access
## on: [push]
on:
####----------------------------------------------------------------------------
  workflow_dispatch:
    name: 'Manual Deployment'
    description: 'Triggering Manual Deployment'
    inputs:
      logLevel:
        description: 'Log level'
        required: true
        default: 'warning'
      tags:
        description: 'Configure Access'
####----------------------------------------------------------------------------
  push:
    branches: [ master ]
    paths:
      - action.yaml
####----------------------------------------------------------------------------
env:
  ## Access KeyPair variables
  PRIVATE_KEYPAIR_FILE: ${{ secrets.PRIVATE_KEYPAIR_FILE }}
  PRIVATE_KEYPAIR_SECRET: ${{ secrets.PRIVATE_KEYPAIR_SECRET }}
####----------------------------------------------------------------------------
jobs:
  provision-access:
    runs-on: ubuntu-latest
    steps:
      - name: checkout
        uses: actions/checkout@v2
####----------------------------------------------------------------------------
      ## Privision Access KeyPair
      - name: Provisioning Access
        uses: ./
        id: provision-access
        with:
          private-keypair-file: ${PRIVATE_KEYPAIR_FILE}
          private-keypair-secret: ${PRIVATE_KEYPAIR_SECRET}
        continue-on-error: false
      - name: Check On Failures
        if: steps.provision-access.outputs.status == 'failure'
        run: |
          echo -e "Warning: Provisioning Access Failed [Status]: ${{ steps.provision-access.outputs.status }}" ;
####----------------------------------------------------------------------------
      ## Display Environment
      - name: Display Environment
        id: display_environment
        run: |
          echo -e "Displaying Enviroment Settings ..." ;
          echo -e "Access KeyPair File: ${PRIVATE_KEYPAIR_FILE}" ;
          echo -e "Access KeyPair Secret: ${PRIVATE_KEYPAIR_SECRET}" ;
```

**<span style="color:red">4</span>** -) The output will be like this: [Pipeline Execution](https://github.com/emvaldes/configure-access/actions?query=workflow%3A%22GitHub+Actions+-+AWS+EC2+Configure+Access%22)

```console
-rw-r--r-- 1 runner docker 3388 Aug 29 21:17 /home/runner/work/configure-access/configure-access/***

AWS Access Key-Pair file length: [3388] ...

Completed!

Displaying Enviroment Settings ...
Access KeyPair File: /home/runner/work/configure-access/configure-access/***
Access KeyPair Secret: /home/runner/work/configure-access/configure-access/***
```

Happy Coding & Share your work!
