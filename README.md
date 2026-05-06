# Pixeldrain to Google Drive Uploader (GitHub Actions)

A professional automation tool designed to transfer files from **Pixeldrain** to **Google Drive** using GitHub Actions runners. This project features high-speed transfer optimization, automatic metadata extraction (MD5 & File Size), and instant Telegram notifications.

## 🚀 Features

- **Automated Transfer**: No need to download files to your local PC.
- **Rclone Integration**: Uses `rclone` for stable and reliable Google Drive uploads.
- **Speed Optimized**: Configured with professional flags (`--drive-chunk-size 64M`) for faster large file uploads.
- **Metadata Extraction**: Automatically calculates **MD5 Checksum** and **File Size**.
- **Telegram Notifications**: Get instant status updates with clickable MD5 hashes directly on your phone.
- **Secure**: All credentials (tokens/configs) are safely stored in GitHub Secrets.

---

## 🛠️ Setup Instructions

### 1. Rclone Configuration
You need to provide your `rclone.conf` data. 
- Run `rclone config` on your local machine to set up a remote named `queen` (or your preferred name).
- Copy the content of your `rclone.conf` file.

### 2. Telegram Bot Setup
- Create a bot via [@BotFather](https://t.me/BotFather) and get the **API Token**.
- Get your **Chat ID** via [@userinfobot](https://t.me/userinfobot).

### 3. GitHub Secrets
Go to your repository **Settings > Secrets and variables > Actions** and add the following secrets:

| Secret Name | Description |
| :--- | :--- |
| `RCLONE_CONF_SECRET` | The entire content of your `rclone.conf` |
| `TELEGRAM_BOT_TOKEN` | Your Telegram Bot API Token |
| `TELEGRAM_CHAT_ID` | Your Telegram Personal Chat ID |

---

## 📖 How to Use

1. Click on the **Actions** tab in this repository.
2. Select the **"Pixeldrain to Google Drive"** workflow on the left sidebar.
3. Click the **"Run workflow"** dropdown button.
4. Input the **Pixeldrain File ID** (The ID is the last part of the URL, e.g., `1234abcd` from `pixeldrain.com/u/1234abcd`).
5. Click **Run workflow**.

Once the process is complete, you will receive a Telegram message containing the file details and the transfer status.

---

## ⚙️ Workflow Details

The workflow performs the following steps:
1. **Prepare**: Sets up a clean temporary environment.
2. **Download**: Pulls the file from Pixeldrain using its API.
3. **Analyze**: Extracts the filename, calculates the MD5 hash, and determines the file size.
4. **Configure**: Initializes `rclone` using your encrypted secret.
5. **Upload**: Sends the file to the `ROM_Builds` folder in your Google Drive with optimized chunk sizes.
6. **Notify**: Sends a formatted HTML message to your Telegram bot.

---

## ⚠️ Limitations & Notes
- **Storage**: Standard GitHub runners provide approximately **14 GB - 20 GB** of free disk space. Ensure your file does not exceed this limit.
- **Security**: The workflow automatically deletes the temporary `rclone.conf` and credentials after the process finishes.
- **Cleanup**: GitHub Actions runners are ephemeral; all temporary data is destroyed immediately after execution.

---

### 📄 License
This project is open-source and free to use.
