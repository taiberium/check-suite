# GitHub Actions for Checks API

[![Build Status](https://api.cirrus-ci.com/github/cirrus-actions/check-suite.svg)](https://cirrus-ci.com/github/cirrus-actions/check-suite) [![](https://images.microbadger.com/badges/version/cirrusactions/check-suite.svg)](https://microbadger.com/images/cirrusactions/check-suite) [![](https://images.microbadger.com/badges/image/cirrusactions/check-suite.svg)](https://microbadger.com/images/cirrusactions/check-suite)

To use the action simply add the following lines to your `.github/main.workflow`:

```
action "Check Suite Passes" {
  uses = "docker://cirrusactions/check-suite:latest"
  env = {
    APP_NAME = "Super App"
  }
}
```

This action will check that a check suite succeeded. See `.github/main.workflow` for a full demo workflow.

### Full `main.workflow` example

![image](https://user-images.githubusercontent.com/989066/47054401-73889380-d166-11e8-8dcb-d72cae4653ca.png)

Let's say a repository has Cirrus CI App installed that uses Checks API to report CI build statuses. Then your 
`.github/main.workflow` can look like this:

```
workflow "Cirrus CI Demo" {
  on = "check_suite"
  resolves = "Cirrus CI Passes"
}

action "Cirrus CI Passes" {
  uses = "docker://cirrusactions/check-suite:latest"
  env = {
    APP_NAME = "Cirrus CI"
  }
}
```
