# Simple Vercel deploy action

![GitHub Release](https://img.shields.io/github/v/release/FedericoGarcia/simple-vercel-deploy-action)
![GitHub License](https://img.shields.io/github/license/FedericoGarcia/simple-vercel-deploy-action)

This action allows you to deploy your project to Vercel with minimal configuration.

## Inputs

### `vercel_team_id`

**Required** The Vercel Organization/Team ID.

### `vercel_project_id`

**Required** The Vercel Project ID.

### `vercel_account_token`

**Required** The Vercel Account Token.

## Examples

### Basic usage

#### `.github/workflows/vercel-deploy.yml`

```yaml
name: Vercel deploy

on:
  push:
    branches:
      - main

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      - name: Vercel deploy
        uses: FedericoGarcia/simple-vercel-deploy-action@v0.1.2
        with:
          vercel_team_id: ${{ vars.VERCEL_TEAM_ID }}
          vercel_project_id: ${{ vars.VERCEL_PROJECT_ID }}
          vercel_account_token: ${{ secrets.VERCEL_ACCOUNT_TOKEN }}
```

### Multiple environments (projects)

#### `.github/workflows/vercel-deploy-development.yml`

```yaml
name: Vercel deploy development

on:
  push:
    branches:
      - development

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      - name: Vercel deploy
        uses: FedericoGarcia/simple-vercel-deploy-action@v0.1.2
        with:
          vercel_team_id: ${{ vars.VERCEL_TEAM_ID }}
          vercel_project_id: ${{ vars.VERCEL_PROJECT_ID_DEVELOPMENT }}
          vercel_account_token: ${{ secrets.VERCEL_ACCOUNT_TOKEN }}
```

#### `.github/workflows/vercel-deploy-production.yml`

```yaml
name: Vercel deploy production

on:
  push:
    branches:
      - production

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      - name: Vercel deploy
        uses: FedericoGarcia/simple-vercel-deploy-action@v0.1.2
        with:
          vercel_team_id: ${{ vars.VERCEL_TEAM_ID }}
          vercel_project_id: ${{ vars.VERCEL_PROJECT_ID_PRODUCTION }}
          vercel_account_token: ${{ secrets.VERCEL_ACCOUNT_TOKEN }}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
