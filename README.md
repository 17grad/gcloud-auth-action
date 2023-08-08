# Google Cloud Auth GitHub Action

This GitHub Action authenticates to Google Cloud and configures Docker to push to Google Container Registry (GCR).

## Requirements

- This action requires the Google Cloud SDK tools to be set up in your runner environment. This can be done using the `google-github-actions/setup-gcloud@v1` action.

## Inputs

### `gcp-credentials`

**Required** - The credentials JSON string for the Google Cloud account. This JSON can be acquired from your GCP Console under the IAM & Admin section.

### `gcp-project-id`

**Required** - The ID of your Google Cloud Project.

### `gcp-artifact-repo`

**Required** - The name of your GCP Artifact Repository.

## Usage

```yaml
name: Deploy to GCR

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Google Cloud Auth
        uses: 17grad/gcloud-auth-action@v1
        with:
          gcp-credentials: ${{ secrets.GCP_CREDENTIALS }}
          gcp-project-id: your-gcp-project-id
          gcp-artifact-repo: your-gcp-artifact-repo
```
Remember to store your GCP credentials as a secret in your repository and refer to them using ${{ secrets.YOUR_SECRET_NAME }}.

## License
Your licensing information here.

## Contributing
Information on contributing to this repo.

