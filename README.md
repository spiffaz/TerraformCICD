# TerraformCICD

This repository contains configurations and scripts for setting up a Terraform Continuous Integration and Continuous Deployment (CICD) pipeline using Jenkins. The pipeline allows you to manage your infrastructure as code and automate the deployment process on AWS.

## Prerequisites

Before you begin, ensure you have the following:

- **Jenkins:** Set up Jenkins on your server or preferred environment.
- **AWS Credentials:** Ensure you have valid AWS access and secret keys stored in Jenkins credentials as 'aws_access_key' and 'aws_secret_access_key'.
- **Terraform:** Install Terraform and configure it in your Jenkins environment. This repository assumes Terraform is installed and available in the Jenkins system path.

## Configuration

### Variables

- `region`: AWS region to deploy resources (default: `us-east-1`).
- `subnet_count`: Number of subnets to create (default: `2`).
- `cidr_block`: CIDR block for the VPC (default: `10.0.0.0/16`).
- `private_subnets`: List of private subnets.
- `public_subnets`: List of public subnets.

### Jenkins Pipeline

The repository includes a Jenkinsfile that defines the CICD pipeline stages:

1. **TerraformInit:** Initializes Terraform in the workspace.
2. **TerraformValidate:** Validates the Terraform configurations.
3. **TerraformPlan:** Creates a Terraform plan and stashes it for later use.
4. **TerraformApply:** Prompts for confirmation and applies the Terraform plan. If confirmation fails, it rolls back by destroying the infrastructure.

Make sure to customize the pipeline according to your project requirements, such as adjusting workspace names, adding additional validation steps, or modifying AWS resource configurations.

## Usage

1. **Clone Repository:** Clone this repository to your local machine or Jenkins server.
2. **Configure Jenkins:** Set up a new Jenkins job and point it to the Jenkinsfile in this repository.
3. **Configure Credentials:** Add your AWS access and secret keys as Jenkins credentials.
4. **Run Pipeline:** Trigger the Jenkins job to run the CICD pipeline. Ensure that the pipeline stages complete successfully.
5. **Monitor:** Monitor the Jenkins job console output for any errors or issues during the pipeline execution.

Feel free to modify and extend the pipeline to suit your specific use case and infrastructure requirements. 

Happy automating!
