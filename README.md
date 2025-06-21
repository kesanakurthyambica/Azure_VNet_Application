## 🔧 Terraform Output Block

```hcl
output "subnet_ids" {
  value = module.app_vnet.vnet_subnets_name_id
}
```

### 📌 Purpose of This Output

This output block exposes the **IDs of the subnets** created within the `app_vnet` module. It allows other modules, scripts, or users to reference these subnet IDs after Terraform has applied the infrastructure.

---

## 📁 Project Overview

### 🎯 Main Purpose

The main purpose of this project is to **automate the provisioning of cloud infrastructure** on Microsoft Azure using **Terraform** and **Azure DevOps Pipelines**. It follows Infrastructure as Code (IaC) principles to ensure consistent, repeatable, and version-controlled deployments.

---

## 🔗 Inputs

Inputs typically come from:

- **Terraform variables** defined in `variables.tf`
- **Module configurations** (e.g., `app_vnet` module)
- **Azure DevOps pipeline parameters**
- **Backend configuration** for remote state

Example input variables might include:

```hcl
variable "vnet_name" {
  type    = string
  default = "my-vnet"
}

variable "subnet_prefixes" {
  type    = list(string)
  default = ["10.0.1.0/24", "10.0.2.0/24"]
}
```

---

## 📤 Outputs

Outputs are defined in `outputs.tf` and are used to:

- Share resource identifiers (like subnet IDs, VM IPs, etc.)
- Pass values between modules
- Enable integration with other tools or scripts

In this case:

```hcl
output "subnet_ids" {
  value = module.app_vnet.vnet_subnets_name_id
}
```

This returns a list of subnet IDs created by the `app_vnet` module.

---

## 💡 Use Cases

Here are some practical use cases for this project:

1. **Environment Provisioning**  
   Automatically create dev, test, or prod environments with consistent configurations.

2. **Multi-Team Collaboration**  
   Share outputs like subnet IDs with other teams (e.g., app or security teams) for further provisioning.

3. **CI/CD Integration**  
   Use Azure DevOps pipelines to plan and apply infrastructure changes as part of a CI/CD workflow.

4. **Security and Compliance**  
   Track infrastructure changes through version control and audit logs.

5. **Scalability**  
   Easily replicate infrastructure across regions or subscriptions using modules and pipelines.
