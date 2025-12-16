# Terraform Project Structure

```
terraform-project/
├── environments/
│   ├── dev/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── terraform.tfvars
│   │   └── backend.tf
│   ├── staging/
│   │   └── [same structure]
│   └── prod/
│       └── [same structure]
├── modules/
│   ├── vpc/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   └── README.md
│   ├── ec2/
│   │   └── [same structure]
│   └── rds/
│       └── [same structure]
├── shared/
│   ├── data.tf
│   └── providers.tf
├── .terraform/
├── .gitignore
├── README.md
├── .cursor/rules
└── .cursorrules
```

## Key Components
- `environments/` - Environment-specific configurations
- `modules/` - Reusable Terraform modules
- `shared/` - Shared resources and provider configs
- `backend.tf` - Remote state configuration
- `variables.tf` - Variable definitions
- `terraform.tfvars` - Variable values (not committed)

## Best Practices
- Use modules for reusable components
- Separate environments
- Use remote state backends
- Version lock providers
- Never commit secrets

