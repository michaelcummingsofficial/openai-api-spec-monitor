# OpenAI API Spec Monitor

A GitHub Action that monitors the [OpenAI API Specification](https://github.com/openai/openai-openapi) for changes. When a change is detected, the diff is analyzed using AI and a PR is created. The PR is automatically merged.

## Community

Join our [Discord Server](https://discord.gg/ZgP524sT2K) to stay updated! The bot sends notifications to the [#openai-api-spec-monitor](https://discord.com/channels/1463555674431684630/1463557477122703424) channel.

## How It Works

1.  Downloads the latest [OpenAI spec](https://raw.githubusercontent.com/openai/openai-openapi/main/openapi.yaml).
2.  Compares the downloaded spec with the spec cached in the repository.
3.  If changes are detected, a summary is generated with AI based on the diff.
4.  A PR is created, using the generated summary, and automatically merged.

## Features

- ⏰ Runs every 30 minutes to check for spec changes.
- ✨ Creates and merges a PR with an AI-generated summary of changes.
- 🔔 Sends a notification to Discord.

## Setup

### Prerequisites

- Discord Webhook URL.
- Vercel AI Gateway API Key.

### Installation

1.  Clone/Fork this repository.

2.  **Create the GitHub App:**

    > A GitHub App is required to bypass branch protection rules (e.g., mandatory reviews) and auto-merge PRs.
    - Go to [Developer Settings](https://github.com/settings/apps) and click **New GitHub App**.
    - Set the name (e.g., `OpenAI API Spec Monitor`) and homepage URL (this repo).
    - Uncheck "Active" under **Webhook**.
    - **Permissions**:
      - Repository permissions > **Contents**: Read and Write
      - Repository permissions > **Pull requests**: Read and Write
    - Create the App.
    - Note the **App ID** (you will need this for the secrets).
    - Generate a **Private Key** and download the `.pem` file (you will need the content of this file).
    - **Install the App**: Click **Install App** on the left menu -> Select your account -> Select this repository.

3.  **Configure Secrets:**
    - Go to your repository `Settings` > `Secrets and variables` > `Actions`.
    - Add the following repository secrets:
      - `GH_APP_ID`: The **App ID** you noted from the GitHub App.
      - `GH_APP_PRIVATE_KEY`: The content of the `.pem` file you downloaded.
      - `AI_GATEWAY_API_KEY`: Your Vercel AI Gateway API key.
      - `DISCORD_WEBHOOK_URL`: Your Discord Webhook URL.
        - _To get this:_ Go to Discord Server settings > **Integrations** > **Webhooks** > **New Webhook**, select channel, copy URL.

4.  **Workflow Permissions:**
    - Go to `Settings` > `Actions` > `General` > `Workflow permissions`.
    - Select "Read and write permissions".

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) for details.
