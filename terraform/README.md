# Voting App Infrastructure

Terraform configuration for a temporary AWS EKS environment for the Voting App DevOps capstone.

## Infrastructure

- One Amazon EKS control plane.
- One managed worker node, initially configured as `t3.medium`.
- IAM roles and policies required by EKS and its worker node.
- Existing subnet tagging for Kubernetes and load-balancer discovery.
- Kubernetes API access restricted by `cluster_endpoint_public_access_cidrs`.

The configuration creates an S3 artifacts bucket with public access blocked, AES-256 server-side encryption, and versioning enabled. The bucket and its associated settings may incur AWS charges. The configuration does not install a monitoring stack in AWS; existing local monitoring remains separate.

## Prerequisites

- Terraform 1.5 or later
- AWS CLI authenticated to the intended account
- Permissions for the required EKS, EC2, IAM, and subnet operations

## Initialize, format, and validate

Run from this directory:

    terraform init
    terraform fmt
    terraform validate

## Review before deployment

Supply a trusted public IPv4 address in CIDR notation (usually your address followed by `/32`) for `cluster_endpoint_public_access_cidrs`. Do not expose the Kubernetes API to `0.0.0.0/0`.

Inspect the subnet IDs and confirm that they exist in the configured AWS region and belong to the intended default VPC.

Then review:

    terraform plan

EKS, worker-node compute, storage, and networking can incur charges. Do not run `terraform apply` until the plan, access permissions, and estimated costs have been reviewed and deployment is explicitly approved.

## Outputs

Terraform reports the AWS region, project name, EKS cluster name and endpoint, and worker node group name.
