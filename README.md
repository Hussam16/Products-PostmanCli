### Automated API Tests using Postman CLI and Notification Check

This GitHub workflow automates API tests using Postman CLI and checks for notifications using Microsoft Teams.

---

### Workflow Overview:

#### Automated API Tests:
- **Trigger:** This job runs on push or release events.
- **Steps:**
  1. **Checkout:** Fetches the repository code.
  2. **Install Postman CLI:** Downloads and installs the Postman CLI.
  3. **Login to Postman CLI:** Authenticates with Postman CLI using the provided API key.
  4. **Run API tests:** Executes the API tests defined in the Postman collection.

#### Check Notification:
- **Name:** Check notification
- **Runs on:** Ubuntu latest
- **Depends on:** Automated API tests job
- **Steps:**
  - **Microsoft Teams Notification:** Sends notifications to Microsoft Teams.
    - **Webhook URL:** Secret containing the Microsoft Teams webhook.
    - **Condition:** Runs always.
    - **Dry Run:** False

---

### Usage:

1. **Postman Collection:**
   - Ensure that the Postman collection ID used in the workflow matches your desired collection.
   - Update the collection ID in the workflow file if necessary.

2. **Secrets:**
   - Ensure that the secrets `POSTMAN_API_KEY` and `MSTEAMS_WEBHOOK` are set in your GitHub repository settings.
   - `POSTMAN_API_KEY`: Postman API key for authentication.
   - `MSTEAMS_WEBHOOK`: Microsoft Teams webhook URL for notifications.

3. **Notification Setup:**
   - Ensure that the Microsoft Teams channel or user where notifications will be sent is configured to receive messages from the provided webhook.

4. **Run Workflow:**
   - Push code changes or create a release to trigger the workflow.
   - View the workflow execution status and test results in the GitHub Actions tab of your repository.

---

### Note:
- Make sure to review and adjust the workflow steps, conditions, and notifications as per your project requirements.
- Ensure proper handling of sensitive data such as API keys and webhook URLs.
- Test the workflow thoroughly in a controlled environment before deploying it to production.

--- 

