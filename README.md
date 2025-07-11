# [Registration url](https://anyrouter.top/register?aff=yAph)

<p align="left">
  <a href="./README.zh-CN.md">
    <img src="https://img.shields.io/badge/-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-blue?style=for-the-badge" alt="简体中文">
  </a>
</p>

# Claude Code CLI Installation and Usage Guide

This guide will walk you through how to install, configure, and use the `@anthropic-ai/claude-code` CLI tool via the `https://anyrouter.top` proxy service.

### 1️⃣ **Install Node.js** (Skip if already installed)

Ensure your Node.js version is `≥ 18.0`.

#### For Ubuntu / Debian Users
```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo bash -
sudo apt-get install -y nodejs
node --version
```

#### For macOS Users
```bash
sudo xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install node
node --version
```

### 2️⃣ **Install Claude Code**

```bash
npm install -g @anthropic-ai/claude-code
claude --version
```

### 3️⃣ **Getting Started**

You will need to configure two environment variables:

*   **Auth Token: `ANTHROPIC_AUTH_TOKEN`**
    After registering on the Anthropic website, go to the **API Keys** page and click **Create Key**. Give it any name, and it's recommended to set the rate limit to "unlimited." Your token will start with `sk-...`.

*   **API Endpoint: `ANTHROPIC_BASE_URL`**
    Use `https://anyrouter.top` as the API service address for this proxy.

In your project directory, run the following commands:

```bash
cd your-project-folder
export ANTHROPIC_AUTH_TOKEN=sk-... 
export ANTHROPIC_BASE_URL=https://anyrouter.top
claude
```

After running `claude`, you will be prompted for initial setup:
*   Select your preferred theme and press Enter.
*   Confirm the safety notice and press Enter.
*   Use the default terminal configuration and press Enter.
*   Trust the current working directory and press Enter.

Now you're ready to start coding with your AI pair programmer in the terminal! 🚀

### 4️⃣ **Configure Environment Variables (Recommended)**

To avoid setting the variables every time you open a new terminal, you can add them to your shell's startup file.

Add the following lines to your `~/.bash_profile`, `~/.bashrc`, and/or `~/.zshrc` file:
```bash
echo -e '\nexport ANTHROPIC_AUTH_TOKEN=sk-...' >> ~/.bash_profile
echo -e '\nexport ANTHROPIC_BASE_URL=https://anyrouter.top' >> ~/.bash_profile

echo -e '\nexport ANTHROPIC_AUTH_TOKEN=sk-...' >> ~/.bashrc
echo -e '\nexport ANTHROPIC_BASE_URL=https://anyrouter.top' >> ~/.bashrc

echo -e '\nexport ANTHROPIC_AUTH_TOKEN=sk-...' >> ~/.zshrc
echo -e '\nexport ANTHROPIC_BASE_URL=https://anyrouter.top' >> ~/.zshrc
```
*(Note: Adding to all three files ensures compatibility with most shell configurations.)*

After restarting your terminal, you can use Claude Code directly:
```bash
cd your-project-folder
claude
```

### ❓ **FAQ**

*   **Note on API Traffic**
    This service acts as a direct proxy for the official Claude Code API. It cannot forward traffic for other, non-Claude Code APIs.

*   **Q: What should I do if I get an API error?**
    A: This might be due to instability in the proxy service. Try exiting Claude Code (`Ctrl+C`) and running it again a few times.

*   **Q: What if I encounter a login error on the website?**
    A: Try clearing the cookies for the site in your browser and logging in again.

*   **Q: How do I fix the `Invalid API Key · Please run /login` error?**
    A: This error means Claude Code did not detect the `ANTHROPIC_AUTH_TOKEN` and `ANTHROPIC_BASE_URL` environment variables. Please double-check that you have configured them correctly.

*   **Q: Why does it show "offline"?**
    A: Claude Code checks its network status by trying to connect to Google. The "offline" status simply means it couldn't reach Google. This **does not affect the normal operation** of Claude Code through our proxy.

*   **Q: Why do web page `fetch` commands fail?**
    A: Before fetching a webpage, Claude Code uses an official Claude service to determine if the page is accessible. To use this feature, you may need an international internet connection (e.g., via a global proxy) to allow access to this validation service.

*   **Q: Why do my requests always show `fetch failed`?**
    A: This could be due to network issues in your region. You can try using a proxy tool or switch to the alternative API endpoint by setting: `export ANTHROPIC_BASE_URL=https://pmpjfbhq.cn-nb1.rainapp.top`
