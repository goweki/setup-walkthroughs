# `gh` GitHub CLI walkthroughs

This file contains walkthroughs and hints for working with the GitHub CLI (`gh`).

## Table of Contents

- [Prerequisites](#prerequisites)
- [Authentication](#authentication)
- [Pull Request](#pull-request)

## Prerequisites

- Ensure you have `gh` (GitHub CLI) installed on your machine. For `Debian`, `Ubuntu Linux`, `Raspberry Pi OS`: You can install using `apt`

    ```bash
    (type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
    && sudo mkdir -p -m 755 /etc/apt/keyrings \
    && wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
    && sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
    && sudo apt update \
    && sudo apt install gh -y
    ```

- You need a GitHub account  .
- Knowledge of Git and GitHub.

## Authentication

### Step 1: Generate a Personal Access Token (PAT) on GitHub.com

- Log in to your GitHub account.
- Navigate to **Settings** > **Developer settings** > **Personal access tokens** > **Tokens (classic/fine-grained)**.
- Click on **Generate new token**.
- Select the appropriate scopes (permissions). For full control over repositories, choose `repo`.
- Click **Generate token**.
- Copy the generated token. **Note:** This token will not be shown again, so save it securely.

### Step 2: Authenticate with `gh` Using the GitHub PAT

To authenticate `gh` using your PAT, follow these steps:

- Open your terminal.
- Run the following command, replacing `YOUR_TOKEN` with the actual token you generated:

    ```bash
    echo YOUR_TOKEN | gh auth login --with-token
    ```
    If the token is valid and has the required scopes, gh will authenticate your session.

### Logout

To select what host and account to log out of via a prompt:

```bash
gh auth logout
```

Log out of a specific host and specific account:

```bash
gh auth logout --hostname enterprise.internal --user monalisa
```


## Pull Request

If authenticated on `gh`, you can create a pull request with the below command. The  Replace the placeholders in **UPPERCASE**

```bash
gh pr create --base BASE --head HEAD --title TITLE --body BODY
```

It uses the current working directory to determine the Git repository you are working with. It looks for the `.git` directory in the current directory or its parent directories.