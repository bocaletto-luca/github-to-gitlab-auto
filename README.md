# GitHub to GitLab Auto Update
#### Author: Bocaletto Luca

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge&logo=gnu)](LICENSE) [![Language: Python](https://img.shields.io/badge/Language-Python-blue?style=for-the-badge&logo=python)](https://www.python.org/) [![Linux-Compatible](https://img.shields.io/badge/Linux-Compatible-blue?style=for-the-badge&logo=linux)](https://www.kernel.org/) [![Status: Complete](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)](https://github.com/bocaletto-luca/Directory-Monitor)

**GitHub to GitLab Auto Update** is a Python-based tool designed to automate the configuration of repository mirroring between your GitHub and GitLab accounts. With this tool, you can automatically import new repositories from GitHub and update existing ones on GitLab, ensuring that the two platforms remain synchronized.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Contributing](#contributing)
- [License](#license)

## Overview

Managing and updating hundreds of repositories manually is time-consuming. This project retrieves all GitLab projects that you are a member of using the GitLab API and automatically sets up mirroring to the corresponding GitHub repositories. By doing so, any update on GitHub is automatically synchronized to GitLab.

- **GitHub Account:** `bocaletto-luca`
- **GitLab Account:** `bocaletto-luca`
- **Project Name:** `github-to-gitlab-auto-update`

## Features

- **Automated Mirroring Setup:** Automatically configures repository mirroring for all your GitLab projects.
- **Bulk Operations:** Efficiently handles a large number (over 220) of repositories.
- **Easy Configuration:** Customize by simply updating a few variables.
- **Secure:** Use personal access tokens (PATs) for authentication with GitHub and GitLab. (Remember to handle your tokens securely!)

## Requirements

- **Python 3.x**
- **Python Module `requests`** (Install via `pip install requests`)
- **Personal Access Tokens:**
  - **GitHub PAT:** Must have the `repo` scope to access private and public repositories.
  - **GitLab PAT:** Must have the `api` scope for modifying project settings.

## Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/bocaletto-luca/github-to-gitlab-auto-update.git
   ```

2. **Navigate to the Project Directory:**

   ```bash
   cd github-to-gitlab-auto-update
   ```

3. **(Optional) Create and Activate a Virtual Environment:**

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

4. **Install Required Dependencies:**

   ```bash
   pip install requests
   ```

## Configuration

Update the configuration variables in the `github_to_gitlab_auto_update.py` file at the beginning of the script:

```python
# Configuration
GITLAB_URL    = "https://gitlab.com/api/v4"
GITHUB_USERNAME = "bocaletto-luca"  # Your GitHub username
GITHUB_TOKEN  = "your_github_token_here"  # Replace with your GitHub Personal Access Token
GITLAB_TOKEN  = "your_gitlab_token_here"   # Replace with your GitLab Personal Access Token
```

> **Security Note:**  
> **Never** commit your tokens in plain text to public repositories. Consider loading these tokens from secure environment variables or a configuration file that is excluded from version control.

## Usage

To start the process and set up mirroring for all your repositories, simply run:

```bash
python3 github_to_gitlab_auto_update.py
```

The script will:
- Retrieve all GitLab projects you are a member of.
- Construct the corresponding GitHub repository URLs.
- Configure each GitLab project with mirroring settings to the GitHub repository.

## How It Works

1. **Fetching Projects:**  
   The script uses the GitLab API endpoint `/projects` to fetch all projects associated with your account. Pagination is handled to ensure all projects are retrieved.

2. **Building Repository URLs:**  
   For every GitLab project, the script constructs the matching GitHub repository URL in this format:  
   `https://github.com/bocaletto-luca/<project_name>.git`  
   Ensure that your GitLab project names match those on GitHub.

3. **Setting Up Mirroring:**  
   The script sends an HTTP PUT request to the GitLab API to configure the mirroring. It passes the GitHub repository URL along with your GitHub credentials (using the PAT) to enable automatic updates.

## Contributing

Contributions, suggestions, and bug reports are greatly appreciated!  
If you have any improvements to propose, please open an issue or submit a pull request.

## License

This project is released under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Created by **bocaletto-luca**

---
