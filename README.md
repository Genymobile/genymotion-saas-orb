# genymotion-saas Orb [![CircleCI Build Status](https://circleci.com/gh/Genymobile/genymotion-saas-orb.svg?style=shield "CircleCI Build Status")](https://circleci.com/gh/Genymobile/genymotion-saas-orb) [![CircleCI Orb Version](https://img.shields.io/badge/endpoint.svg?url=https://badges.circleci.io/orb/genymotion/genymotion-saas)](https://circleci.com/orbs/registry/orb/genymotion/genymotion-saas) [![GitHub License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://raw.githubusercontent.com/Genymobile/genymotion-saas-orb/master/LICENSE) [![CircleCI Community](https://img.shields.io/badge/community-CircleCI%20Discuss-343434.svg)](https://discuss.circleci.com/c/ecosystem/orbs)

Use this orb to easily start Genymotion Android virtual devices, connect through ADB and stop devices on [Genymotion Cloud SaaS](https://cloud.geny.io) for mobile automation testing.

## Usage

See [this orb's listing in CircleCI's Orbs Registry](https://circleci.com/orbs/registry/orb/genymotion/genymotion-saas) for details on usage, or see below example:

## Example

In this example `config.yml` snippet, the required Genymotion Cloud SaaS secrets (GMCLOUD_SAAS_EMAIL, GMCLOUD_SAAS_EMAIL) are stored as environment variables and then read as default parameter values by the `genymotion-saas/setup` command.

```yaml
version: 2.1

orbs:
  genymotion-saas: genymotion/genymotion-saas@x.y

jobs:
  android:
    executor: genymotion-saas/default
    steps:
      - genymotion-saas/setup
      - genymotion-saas/start-instance:
          recipe_uuid: "" # Mandatory: Retrieve the recipe uuid using 'gmsaas recipes list' command line or check https://support.genymotion.com/hc/en-us/articles/360007473658-Supported-Android-devices-templates-for-Genymotion-Cloud-SaaS for a comprehensive list of all currently available recipes UUIDs.
      - run: echo "Run your tests here"
      - genymotion-saas/stop-instance

workflows:
  version: 2
  build:
    jobs:
      - android
```
