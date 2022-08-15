# Github Reusable Workflows

Collection of reusable GitHub Action workflows.

## Generate Artifact Tag

Generates StreetShares artifact tag.

### Usage

```yaml
tag:
  uses: streetshares/github-reusable-workflows/.github/workflows/artifact-tag.yaml@main
  secrets: inherit
job:
  needs: tag
  steps:
    - run: echo ${{needs.tag.outputs.tag}}

```

| Attribute           | Type   | Required | Default |
| ------------------- | ------ | -------- | ------- |
| BUILD_TAGGING_TOKEN | secret | true     |         |
| tag                 | output |          |         |

## SonarQube Upload

Uploads previously uploaded files with `actions/upload-artifact` github action.

```yaml
jobs:
  sonarqube:
    needs: [pytest]
    name: SonarQube Analysis
    uses: streetshares/github-reusable-workflows/.github/workflows/sonarqube.yaml@main
    with:
      upload-name: coverage-report
    secrets: inherit
```

| Attribute      | Type   | Required | Default         |
| -------------- | ------ | -------- | --------------- |
| upload-name    | input  | false    | coverage-report |
| SONAR_TOKEN    | secret | true     |                 |
| SONAR_HOST_URL | secret | true     |                 |
