# common-workflows
A main repo for all of our reusable github workflows

## How to use

### Deploy

When you add a new training script you should add workflows in `.github/workflows` and in the jobs section it should look like

```
jobs:
  deploy-staging:
    uses: viam-modules/common-workflows/.github/workflows/deploy_training_script.yaml@main
    with:
      framework: tflite
      script_name: classification-tflite
      type: tflite
      org_id: e76d1b3b-0468-4efd-bb7f-fb1d2b352fcb
    secrets: inherit
```

This will call our shared `deploy_training_script` workflow with the necessary inputs.


### Pull Request

When you add a new training script you should add workflows in `.github/workflows` and in the jobs section it should look like

```
jobs:
  build:
    uses: viam-modules/common-workflows/.github/workflows/pull_request.yaml@main
    with:
      script_name: classification-tflite
```