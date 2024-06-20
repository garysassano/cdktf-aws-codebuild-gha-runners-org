# cdktf-aws-codebuild-gha-runners-org

CDKTF app  that deploys a GitHub repository within an organization, along with an organization webhook that triggers [CodeBuild-hosted GitHub Actions runners](https://docs.aws.amazon.com/codebuild/latest/userguide/action-runner.html) when workflow jobs are queued.

### Related Apps

- [cdktf-aws-codebuild-gha-runners](https://github.com/garysassano/cdktf-aws-codebuild-gha-runners) - Uses a GitHub repository webhook instead of organization webhook.
- [cdk-aws-codebuild-gha-runners](https://github.com/garysassano/cdk-aws-codebuild-gha-runners) - Uses a GitHub repository webhook instead of organization webhook; built with AWS CDK instead of CDKTF.

## Prerequisites

- **_AWS:_**
  - Must have authenticated with [Default Credentials](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#authentication-and-configuration) in your local environment.
- **_GitHub:_**
  - Must have set the `GITHUB_TOKEN` and `GITHUB_OWNER` variables in your local environment.
- **_Terraform:_**
  - Must be [installed](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli#install-terraform) in your system.
- **_Node.js + npm:_**
  - Must be [installed](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) in your system.

## Installation

```sh
npx projen install
```

## Deployment

```sh
npx projen deploy
```

## Usage

1. Access the GitHub Actions workflow by clicking the `<GHA_WORKFLOW_URL>` from the deployment outputs:

   ```sh
   Outputs:
   GhaWorkflowUrl = <GHA_WORKFLOW_URL>
   ```

2. Click `Run workflow` ➜ `Run workflow`.

3. Your workflow will be enqueued and run on an ephemeral EC2 instance managed by AWS CodeBuild.

## Cleanup

```sh
npx projen destroy
```

## Architecture Diagram

![Architecture Diagram](./src/assets/arch-diagram.svg)
