# Github Reusable Workflows

Collection of reusable GitHub Action workflows.

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

| Input              | Type   | Required | Default         |
| ------------------ | ------ | -------- | --------------- |
| upload-name        | with   | false    | coverage-report |
| sonarqube-token    | secret | true     |                 |
| sonarqube-host-url | secret | true     |                 |
