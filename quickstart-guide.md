# DocuSync CLI — Quick Start Guide

This guide will help you install the DocuSync Command Line Interface (CLI) and synchronize your first local project directory with the DocuSync Cloud in less than 5 minutes.

## Prerequisites

Before starting, ensure you have the following requirements:

*   **Operating System:** macOS (12.0 or higher), Linux (Ubuntu 20.04+), or Windows 10/11.
*   **Node.js:** Version 18.0 or higher installed. Check your version by running `node -v`.
*   **Account:** A valid active account at [DocuSync Cloud](https://example.com).

---

## Step 1: Install the CLI

Install the DocuSync CLI globally on your system using `npm`. Open your terminal or command prompt and execute the following command:

```bash
npm install -g @docusync/cli
```

*Note for Linux/macOS users: If you encounter permission errors, you may need to run the command with administrator privileges:* `sudo npm install -g @docusync/cli`.

---

## Step 2: Authenticate your Account

To connect the CLI to your cloud workspace, you need to log in. Run the login command:

```bash
docusync login
```

1. Your default web browser will automatically open the DocuSync login page.
2. Enter your credentials and click **Authorize**.
3. Once authenticated, close the browser window. Your terminal will display a success message: `✓ Successfully authenticated as user@example.com`.

---

## Step 3: Initialize your Project Directory

Navigate to the local folder you want to keep synchronized and initialize the DocuSync configuration.

```bash
cd /path/to/your/local-folder
docusync init
```

The CLI will prompt you for a project name. Type your preferred name and press `Enter`. This creates a hidden configuration file (`.docusync.json`) inside your directory.

---

## Step 4: Run your First Synchronization

To upload your local files to the cloud for the first time, execute the `sync` command:

```bash
docusync sync
```

### Expected Output
The CLI will scan your folder and start uploading files. You will see a progress bar in your terminal:

```text
Scanning repository... Found 14 files.
[========================================] 100% | Uploading files
✓ Sync complete. 14 files uploaded successfully.
```

---

## Troubleshooting & Next Steps

*   **Files not uploading?** Check if your files are listed in a `.gitignore` or `.docusyncignore` file, as the CLI skips ignored extensions by default.
*   **Need more commands?** Run `docusync --help` to explore advanced options like automatic sync intervals and conflict resolution strategies.
