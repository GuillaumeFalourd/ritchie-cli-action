# Ritchie CLI Action

[![Action test on Ubuntu](https://github.com/GuillaumeFalourd/ritchie-cli-action/actions/workflows/ubuntu.yml/badge.svg)](https://github.com/GuillaumeFalourd/ritchie-cli-action/actions/workflows/ubuntu.yml) [![Action test on MacOs](https://github.com/GuillaumeFalourd/ritchie-cli-action/actions/workflows/macos.yml/badge.svg)](https://github.com/GuillaumeFalourd/ritchie-cli-action/actions/workflows/macos.yml) [![Action test on Windows](https://github.com/GuillaumeFalourd/ritchie-cli-action/actions/workflows/windows.yml/badge.svg)](https://github.com/GuillaumeFalourd/ritchie-cli-action/actions/workflows/windows.yml)

<img width="1000" alt="title" src="https://user-images.githubusercontent.com/22433243/123156441-aa4af780-d43f-11eb-8f1c-b7a8d4d536be.png">

Github Action to run [Ritchie CLI](https://ritchiecli.io) commands on any OS runner ⚙️🖥

* * *

## 📚 Usage

### Requirements

⚠️  The [`actions/checkout`](https://github.com/actions/checkout) is mandatory to use this action on **`WINDOWS RUNNER`**, as the repository root is used to install and execute Ritchie binary.

⚠️ [`Actions to setup environments`](https://github.com/marketplace?type=actions&query=setup+env+) may be necessary to use this action depending on the `runner` or the `programming language` that will be used to run or build the formula. For example:

- [setup-node](https://github.com/marketplace/actions/setup-node-js-environment) for formula coded using Node, 
- [setup-go](https://github.com/marketplace/actions/setup-go-environment) for formula code using Golang, 
- [setup-java](https://github.com/marketplace/actions/setup-java-jdk) for formula coded using Java
- ...

 * * *

## ♻️ Scenarios

#### Run rit formula from PUBLIC Github repository

```yaml
    steps:
      - uses: GuillaumeFalourd/ritchie-cli-action@v1
        with:
          args: demo coffee-python --rit_name=Dennis --rit_coffee_type=espresso --rit_delivery=false
          rit_repo_url: https://github.com/ZupIT/ritchie-formulas-demo
```

#### Run rit formula from PRIVATE Github repository

```yaml
    steps:
      - uses: GuillaumeFalourd/ritchie-cli-action@v1
        with:
          args: python math sum numbers --number_one=1 --number_two=2
          rit_repo_url: https://github.com/GuillaumeFalourd/formulas-training
          access_token: ${{ secrets.ACCESS_TOKEN }}
```

* * *

## ▶️ Action Inputs

Field | Mandatory | Observation
------------ | ------------  | -------------
**args** | YES | Ritchie formula command line **WITHOUT** `rit` prefix and **WITH** `input flags`. <br/> _e.g: `demo hello-world`_
**rit_repo_url** | YES | Github repository where the formula's code is located. <br/> _e.g: `https://github.com/ZupIT/ritchie-formulas-demo`_
**access_token** | NO | Github [Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) with access to the private formulas repository to import.

* * *

## Licensed

This repository uses the [Apache License 2.0](https://github.com/GuillaumeFalourd/aws-cliaction/blob/main/LICENSE)
