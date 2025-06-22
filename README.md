# Satellite-utils

## Automated Satellite with Ansible



# 📚 Satellite-utils - Tasks
This repository contains Ansible tasks designed to manage and automate operations on Red Hat Satellite servers. Below is a detailed description of each available task.

## Task: **cleanup_content_views.yml**
Description:
Cleans up old content view versions for a specified organization in Red Hat Satellite, retaining only a defined number of recent versions.

Steps:

1. Executes the content view version cleanup using the role redhat.satellite.content_view_version_cleanup.

2. Sends a Slack notification indicating success or failure.

Slack Notification:

- Success: Sends a message informing that the cleanup was completed successfully.

- Failure: Sends a message indicating that the cleanup has failed.

## Task: **repository_list.yml**
Description:
Lists all repositories from the Red Hat Satellite server for a given organization by paginating through the API.

Steps:

1. Retrieves a page of repository data via Satellite's API.

2. Appends the repository label and its last synchronization result to a fact (result_values).

## Task: **repository_status.yml**
Description:
Checks the synchronization status of all repositories in a given organization.

Steps:

1. Determines the total number of pages of repositories.

2. Iteratively loads and lists repositories using repository_list.yml.

3. Displays the collected repository synchronization results.

4. Sends a Slack notification:

   - If any repository failed to synchronize, lists the failed repositories.

   - If all repositories are synchronized successfully, sends a confirmation message.

## Task: **repository_sync.yml**
Description:
Triggers the synchronization of all repositories defined by the variable ui_sat_products.

Steps:

1. Loops through each product name defined in ui_sat_products.

2. Initiates synchronization for each product using the module redhat.satellite.repository_sync.



# Requirements
- Red Hat Satellite server

- Ansible collections:

  - redhat.satellite

  - community.general (for Slack notifications)

- Slack token (if Slack notifications are required)


# Author
### [Caio Silveira](https://www.linkedin.com/in/caiosilveira/)