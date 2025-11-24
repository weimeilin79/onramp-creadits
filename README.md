# onramp-creadits

This repository contains a template and automation scripts designed to streamline the process of linking a user's Google Cloud project with a billing account. It automates the setup of a new Google Cloud project (or uses an existing one) and enables billing, which is a common prerequisite for many codelabs and workshops.

## What this script does

The `init.sh` script automates the following steps to prepare the environment:

1.  **Project Verification/Creation**:
    *   Checks for an existing project ID in `~/project_id.txt`.
    *   If found, verifies access to the project.
    *   If not found, prompts the user to create a new project (defaulting to a generated ID based on `CODELAB_PROJECT_PREFIX`).
2.  **Environment Setup**:
    *   Sets the active project in the `gcloud` configuration.
    *   Installs necessary Python dependencies (specifically `google-cloud-billing`).
3.  **Billing Enablement**:
    *   **Reads Project ID**: Retrieves the project ID from the file created by `init.sh`.
    *   **Enables Billing API**: Ensures the Cloud Billing API is enabled for the project.
    *   **Fetches Accounts**: Lists available billing accounts, handling permissions and propagation delays.
    *   **Links Project**: Selects the first open billing account and links the project to it.
    *   **Verifies Link**: Confirms the link is active and billing is enabled.

## Prerequisites

Before you begin, you must claim your cloud credits:

1.  **Claim Credits**: Ask the user to claim their Google Cloud credits via the OnRamp portal. This is essential to ensure they have a valid billing account to link.


## Configuration

Before running the setup script, you need to configure the project prefix:

1.  Open `init.sh`.
2.  Locate the `CODELAB_PROJECT_PREFIX` variable (around line 40).
3.  Edit the value to match your specific codelab or project needs.
    ```bash
    CODELAB_PROJECT_PREFIX="your-codelab-prefix"
    ```

## Setup

1.  **Import Repository**: Have the user import your forked repository into their environment (e.g., Cloud Shell Editor).


## Usage

### Must have these in your Codelab Instruction

👉💻 Run the setup script from the project directory.

> **⚠️ Note on Project ID:**
> The script will suggest a randomly generated default Project ID. You can press **Enter** to accept this default.
>
> However, if you prefer to **create a specific new project**, you can type your desired Project ID when prompted by the script.

```bash
cd ~/YOUR_REPO_HOME_DIR
./init.sh
```

The script will handle the rest of the setup process automatically.

> **👉 Important Step After Completion:**
> Once the script finishes, you must ensure your Google Cloud Console is viewing the correct project:
> 1. Go to [console.cloud.google.com](https://console.cloud.google.com/).
> 2. Click the project selector dropdown at the top of the page.
> 3. Click the **"All"** tab (as the new project might not appear in "Recent" yet).
> 4. Select the Project ID you just configured in the `init.sh` step.
