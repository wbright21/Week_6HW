# Week_6HW
# Class 7 Week 6 Starting Terraform Guide

This document captures the essential, step-by-step instructions from the class for successfully initializing a Terraform project, authenticated to your AWS account.

## A. Technical Aspects: Step-by-Step Terraform Initialization Guide

This guide details the precise, concrete actions and settings discussed in the class, allowing a reader to replicate the setup exactly.

### I. Prerequisites and Initial Configuration

1. **Verify AWS CLI Configuration:**
   a.  Open your command line interface (CLI): **Git Bash** (Windows) or **Terminal** (Mac).
   b.  Execute the command: `aws configure`.
   c.  Verify that your **AWS Access Key ID**, **AWS Secret Access Key**, **Default region name**, and **Default output format** are present and correct.
   d.  **Crucial Note:** Terraform uses these stored keys for authentication. If the keys are not configured, Terraform cannot authenticate to AWS. Resolve any missing configurations with your group before proceeding.

2. **Verify Terraform Installation:**
   a.  In your CLI, check the installed version: `terraform --version`.
   b.  **Note on Version:** The output may indicate your version is slightly out of date. This is acceptable; do not stop or alert the class, as long as Terraform is successfully installed.
   c.  *Optional Upgrade Commands:*
   i.  **Mac/Linux (Homebrew):** Run `brew update` followed by `brew upgrade`.
   ii. **Windows (Chocolatey):** Run `Choco upgrade all` or `Choco upgrade terraform`.

3. **Create and Navigate to the Project Directory (Folder):**
   a.  Create a **new, empty folder** for your project.
   b.  **Mandatory Naming Convention:** The folder name must be **one word**, contain **no spaces**, and use **no capital letters** (e.g., `2025oct14`).
   c.  **Mandatory Location:** **Do NOT** create this folder inside **OneDrive**. Ensure it is on your local PC.
   d.  Right-click inside this empty folder and select **Open Git Bash here**.

### II. Terraform File Creation and Preparation

4. **Create the Initial Authentication File:**
   a.  Using the Git Bash terminal open in the new folder, create an empty Terraform file. The file name convention uses a zero prefix to indicate its sequential importance.
   b.  Command: `touch 0-auth.tf`
   c.  (Optional Verification) Run `ls` to confirm the file exists, or `cat 0-auth.tf` to confirm it is empty.

5. **Open the Project in Visual Studio Code (VS Code):**
   a.  From the same Git Bash terminal, open the entire current directory in VS Code: `code .`

6. **Insert Authentication Code:**
   a.  Access the instructor's **GitHub repository** (or your forked version) to find the example file named `0-auth.tf`.
   b.  Copy the code contents of the raw file.
   c.  Paste this code into your local, empty `0-auth.tf` file within VS Code.

7. **Save the Terraform File (CRITICAL STEP):**
   a.  You **must save** the file for Terraform to read its contents.
   b.  Use the shortcut: **Ctrl+S** (Windows) or **Cmd+S** (Mac).

8. **Configure Git Bash Default (Windows Users):**
   a.  If your VS Code terminal defaults to **PowerShell** (which is not recommended for this class), change it to **Git Bash**.
   b.  In VS Code, go to **Terminal > Select Default Profile**, and choose **Git Bash**.

9. **Download the `.gitignore` File (To be run in Git Bash):**
   a.  To protect sensitive and auto-generated files from being accidentally pushed to your remote repository, run the following command provided by the Admin (Aaron) to download a standard `.gitignore` file:
   `curl -o .gitignore https://raw.githubusercontent.com/Aaron-Rob/terraform-aws/master/.gitignore`
   b.  **Do NOT touch or modify** the contents of the `.gitignore` file.

### III. Execution and Validation

10. **Initialize Terraform (Starting the Engine):**
    a.  Run the initialization command. This command is required every time you start a new Terraform project in an empty folder or add a new provider/module.
    b.  Command: `terraform init`
    c.  **Expected Result:** This command initializes the backend and provider plugins, creating two new files/folders in your directory:
    i. The **.terraform** subfolder.
    ii. The **.terraform.lock.hcl** file.

11. **Perform Configuration Validation:**
    a.  Check the file for syntactical correctness before attempting to interact with the cloud.
    b.  Command: `terraform validate`
    c.  **Expected Result:** `Success! The configuration is valid.`

12. **Generate an Execution Plan:**
    a.  This command shows what changes Terraform *proposes* to make to your cloud environment.
    b.  Command: `terraform plan`

13. **Apply the Configuration:**
    a.  Execute the proposed changes.
    b.  Command: `terraform apply`
    c.  **Expected Result:** Since the `0-auth.tf` file only authenticates the provider and contains no resources, the output should show: `Apply complete! Resources: 0 added, 0 changed, 0 destroyed.`
    d.  **Creation of State File (CRITICAL WARNING):** Successfully running `terraform apply` creates the **terraform.tfstate** file.
    e.  **ABSOLUTELY DO NOT TOUCH, MODIFY, OR ERASE** the **terraform.tfstate** file. This file tracks the real state of your cloud resources, and modifying it will cause chaos and destruction.

### IV. Files Not to Touch

| File/Folder Name | Description | Instruction |
| :--- | :--- | :--- |
| **`.terraform`** (folder) | Subfolder created by `terraform init` containing necessary binaries/plugins. | **Do Not Touch.** |
| **`terraform.lock.hcl`** (file) | Locks provider versions for consistent deployment. | **Do Not Touch.** |
| **`.gitignore`** (file) | Protects sensitive files from being pushed to GitHub. | **Do Not Touch.** |
| **`terraform.tfstate`** (file) | The core state file tracking cloud resources. | **Do Not Touch (Extremely Sensitive).** |
```eof


