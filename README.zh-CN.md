# [注册地址](https://anyrouter.top/register?aff=yAph)

<p align="left">
  <a href="./README.md">
    <img src="https://img.shields.io/badge/-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-blue?style=for-the-badge" alt="English">
  </a>
</p>

# Claude Code 命令行工具安装与使用指南

本指南将引导您如何安装和配置 `@anthropic-ai/claude-code` 命令行工具，并通过 `https://anyrouter.top` 代理服务进行使用。

## 1️⃣ 第一步：安装 Node.js（已安装可跳过）

请确保您的 Node.js 版本不低于 `18.0`。

<details>
<summary><strong>Ubuntu / Debian 用户</strong></summary>

```sh
# 安装 Node.js
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo bash -
sudo apt-get install -y nodejs

# 验证版本
node --version
```
</details>

<details>
<summary><strong>macOS 用户 (使用 Homebrew)</strong></summary>

```sh
# 安装 Homebrew (如果尚未安装)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 安装必要的 Xcode 命令行工具
sudo xcode-select --install

# 使用 Homebrew 安装 Node.js
brew install node

# 验证版本
node --version
```
</details>

## 2️⃣ 第二步：安装 Claude Code

使用 `npm` 全局安装 Claude Code 工具。

```sh
npm install -g @anthropic-ai/claude-code
```

安装完成后，运行以下命令验证是否成功：

```sh
claude --version
```

## 3️⃣ 第三步：开始使用

在开始之前，您需要配置两个关键的环境变量。

1.  **获取 Auth Token (`ANTHROPIC_AUTH_TOKEN`)**
    *   注册 Anthropic 账号后，在 [API令牌](https://console.anthropic.com/settings/keys) 页面点击 **添加令牌** 获得。
    *   API 令牌以 `sk-` 开头。
    *   **名称**：随意填写。
    *   **额度**：建议设为无限额度。
    *   其他保持默认设置即可。

2.  **设置 API 地址 (`ANTHROPIC_BASE_URL`)**
    *   本教程使用的代理服务地址为 `https://anyrouter.top`。

在您的项目目录下，执行以下命令启动 Claude Code：

```sh
# 进入您的项目文件夹
cd your-project-folder

# 设置环境变量 (仅在当前终端会话中有效)
export ANTHROPIC_AUTH_TOKEN=sk-... 
export ANTHROPIC_BASE_URL=https://anyrouter.top

# 启动 Claude Code
claude
```

首次运行后，根据提示完成初始化设置：
*   选择你喜欢的主题 + `Enter`
*   确认安全须知 + `Enter`
*   使用默认 Terminal 配置 + `Enter`
*   信任工作目录 + `Enter`

现在，您就可以开始在终端里和您的 AI 编程搭档一起写代码了！🚀

## 4️⃣ 第四步：配置永久环境变量（推荐）

为避免每次启动终端时都需要重复设置环境变量，建议将其写入您 Shell 的配置文件中。

**根据您使用的 Shell，选择对应的命令执行：**

```sh
# 对于 Bash 用户 (常见于 Linux 和旧版 macOS)
echo -e '\n# Claude Code Configuration' >> ~/.bashrc
echo 'export ANTHROPIC_AUTH_TOKEN=sk-...' >> ~/.bashrc
echo 'export ANTHROPIC_BASE_URL=https://anyrouter.top' >> ~/.bashrc

# 对于 Zsh 用户 (常见于新版 macOS)
echo -e '\n# Claude Code Configuration' >> ~/.zshrc
echo 'export ANTHROPIC_AUTH_TOKEN=sk-...' >> ~/.zshrc
echo 'export ANTHROPIC_BASE_URL=https://anyrouter.top' >> ~/.zshrc

# 为了兼容性，也可以添加到 .bash_profile
echo -e '\n# Claude Code Configuration' >> ~/.bash_profile
echo 'export ANTHROPIC_AUTH_TOKEN=sk-...' >> ~/.bash_profile
echo 'export ANTHROPIC_BASE_URL=https://anyrouter.top' >> ~/.bash_profile
```

**重要提示**：请将 `sk-...` 替换为您自己的真实 API 令牌。

配置完成后，**重启您的终端**。之后，您只需进入项目目录并运行 `claude` 即可使用。

```sh
cd your-project-folder
claude
```

---

## ❓ 常见问题 (FAQ)

**Q: 报错 `Invalid API Key · Please run /login` 怎么解决？**
A: 这个错误表明 Claude Code 没有检测到 `ANTHROPIC_AUTH_TOKEN` 和 `ANTHROPIC_BASE_URL` 环境变量。请仔细检查您的环境变量是否已按照 **第四步** 正确配置并已重启终端。您可以通过运行 `echo $ANTHROPIC_AUTH_TOKEN` 来检查变量是否生效。

**Q: 为什么状态显示 `offline`？**
A: Claude Code 会通过尝试连接 Google 来判断网络状态。在中国大陆环境下，这通常会失败，导致显示 `offline`。**这并不影响工具的正常使用**，只要您的代理 API 地址可访问即可。

**Q: 为什么浏览网页（Fetch）功能会失败？**
A: 这是因为 Claude Code 在访问网页前，会先调用 Claude 的一个内部服务来判断网页内容是否安全。这个内部服务需要国际互联网连接。如果您需要使用此功能，请确保您的终端环境已配置全局代理。

**Q: 为什么请求总是显示 `fetch failed`？**
A: 这很可能是因为您所在地区的网络环境无法稳定连接到 API 代理服务器。您可以尝试使用备用的 API 地址：
```sh
export ANTHROPIC_BASE_URL=https://pmpjfbhq.cn-nb1.rainapp.top
```

**Q: 关于本站的 API 代理服务**
A: 本站 (`https://anyrouter.top`) 仅直接转发官方 Claude Code 的 API 流量，无法用于其他非 Claude Code 的 API 请求。如遇 API 报错，可能是转发代理不稳定，可以尝试退出 Claude Code (`/quit` 或 `Ctrl+C`) 并重试几次。

**Q: 网页登录遇到问题怎么办？**
A: 如果在 Anthropic 官网或代理服务网站登录时遇到问题，可以尝试清除该网站的 Cookie 后重新登录。
