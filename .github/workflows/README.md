# Github Actions Workflows for this project

This file contains documentation related to the use of workflows to manage code
checks and deployments for this project.

All Github Actions workflows are stored in the .github/workflows directory
within the targeted repository.  Workflows are defined as .yml files, following
a specified syntax.

## Template

This project contains a workflow template that has documentation references
included as comments to help with the creation of actual workflows for this
project.  The template contains the minimum setup and preliminary required
checks for any workflow used in this project, along with documentation in the
form of comments embedded within the template on requirements for setup,
structure and required/optional components as well as reference links to
relevant Github documentation for Github Actions.

## Repository-level environment secrets.

Before workflows using this template can be created, there are some environment
secrets that need to be created at the repository level (or the organization 
level) for any workflow created in this repository template to execute 
properly.  These secrets can be set at the organization level if you want to
make them available to multiple repositories.

To create repository level variables, you must be a repository owner.  See
[this documentation](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) 
for detailed instructions on creating environment secrets.

The specific secret names and values to be used are as follows (details on
the secrets are included in the template comments):

* ACQUIA_API_KEY
* ACQUIA_API_SECRET
* PRIVATE_SSH_KEY

The Acquia API Key and Secret are needed for ACLI to authenticate to Acquia Cloud for
deployments.  Instructions for setting an Acquia API key and secret can be found
at https://docs.acquia.com/acquia-cloud-platform/develop-apps/api/auth

The PRIVATE_SSH_KEY is needed to push code to the Acquia Git repository.

All three of these values should be created on the user account that will be used for
deployments.  It is recommended that this user account NOT be tied to a "live" user, for
security purposes and to keep from breaking the deployment pipelin in the event that a 'live'
user's keys are revoked, which can happen whan a user leaves an organization and their
access is removed from your Acquia Cloud account.

This user will need to have sufficient privileges to conduct deployments, which is usually
at the Team Lead level or higher.
