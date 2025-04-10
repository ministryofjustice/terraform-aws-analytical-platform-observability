# Analytical Platform Observability Terraform Module

[![Ministry of Justice Repository Compliance Badge](https://github-community.service.justice.gov.uk/repository-standards/api/terraform-aws-analytical-platform-observability/badge)](https://github-community.service.justice.gov.uk/repository-standards/terraform-aws-analytical-platform-observability)

[![Open in Dev Container](https://raw.githubusercontent.com/ministryofjustice/.devcontainer/refs/heads/main/contrib/badge.svg)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/ministryofjustice/terraform-aws-analytical-platform-observability)

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/ministryofjustice/terraform-aws-analytical-platform-observability)

This Terraform module provisions the required resources for Analytical Platform's Grafana to read CloudWatch.

## Usage

```hcl
module "analytical_platform" {
  source = "github.com/ministryofjustice/terraform-aws-analytical-platform-observability?ref=<version>"

  enable_cloudwatch_read_only_access    = true
  enable_amazon_prometheus_query_access = true
  enable_aws_xray_read_only_access      = true

  additional_policies = {
    managed_prometheus_kms_access = module.managed_prometheus_kms_access_iam_policy.arn
  }

  tags = local.tags
}
```

## Testing

```bash
make test
```
