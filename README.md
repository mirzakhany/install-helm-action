# Install helm and kubectl

Install helm and kubectl.

## Inputs

### `helm_version`
**Optional** - helm version to install. will use the latest version if not provided

### `kubectl_version`
**Optional** - kubectl version to install. will use the latest version if not provided

### `k8s_config`
**Required** - Base64 encoded k8s config.

## Example usage

```yaml
# .github/workflows/deploy.yml
name: Deploy
on:
  pull_request:
    types:
      - closed

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - uses: mirzakhany/install-helm-action@v1
        with:
          k8s_config: ${{ secrets.K8S_CONFIG_B64 }}

      - name: deploy app
        shell: bash
        run: helm install --namespace=apps release-name ./helm-chart
```
