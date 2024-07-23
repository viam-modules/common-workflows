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
      model_type: tflite
    secrets: inherit
```

This will call our shared `deploy_training_script` workflow with the necessary inputs.


### Linting/Testing in Pull Requests

When you add a new training script you should add workflows in `.github/workflows` and in the jobs section it should look like

```
jobs:
  build:
    uses: viam-modules/common-workflows/.github/workflows/lint_and_test.yaml@main
    with:
      test_script_name: scripts/test.sh
```

### Secrets

These workflows require a few secrets. They have already been set up as github secrets for the `viam-modules` org. So you shouldn't need to do anything special in your new repo. But for transparency, they can be found:
 - API_KEY_ID and API_KEY: This is done using an API key that belongs to the `viam-dev` environment. These can be found by going to app.viam.com -> go to the `viam-dev` org -> Settings -> Find the keys named GITHUB_VIAM_MODULES.
 - ORG_ID: This is `organization_id` for `viam-dev`. This can be found by navigating to Settings in app.viam.com and finding the `organization_id`.