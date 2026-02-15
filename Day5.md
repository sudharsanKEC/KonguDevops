# Day 5 Documentation

## Installation Commands

```bash
# Install necessary packages
sudo apt-get update
sudo apt-get install -y package_name
```

## Project Structure

```
├── src/                # Source files
│   ├── main.py        # Main application code
│   └── utils.py       # Utility functions
├── config/             # Configuration files
│   ├── config.yml     # Configuration settings
│   └── secrets.yml    # Sensitive information
└── README.md           # Project documentation
```

## Configuration Files

- **config.yml**: Contains project settings and environment variables.
- **secrets.yml**: Holds sensitive data such as API keys and passwords.

## Terraform Workflow Steps

1. **Initialize Terraform**: Run `terraform init` to initialize the configuration.
2. **Plan**: Generate the execution plan using `terraform plan`.
3. **Apply**: Apply the changes to create resources with `terraform apply`.
4. **Destroy**: Clean up and remove all resources using `terraform destroy`.

---