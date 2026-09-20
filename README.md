# Server Keep-Alive

This repository uses **GitHub Actions** to automatically ping a target URL every 10 minutes.  
It helps keep free-tier servers (Render, Railway, Streamlit Cloud, etc.) from sleeping.

## How it works

- A GitHub Actions workflow runs every 10 minutes.
- It sends a strong HTTP request (with cache-busting headers) to the URL stored in a GitHub secret.
- You never need to keep anything running on your computer.

## Setup Instructions

1. Create a new GitHub repository and push these files.
2. Go to your repository → **Settings** → **Secrets and variables** → **Actions**.
3. Click **New repository secret**.
4. Name: `TARGET_URL`
5. Value: your full URL (example: `https://backend-lszx.onrender.com`)
6. Save the secret.

That’s it. The workflow will start running automatically.

## Manual Test

Go to the **Actions** tab → select **Keep Server Alive** → click **Run workflow**.

## Notes

- GitHub free accounts have a limit of ~2000 minutes/month.  
  Running every 10 minutes uses roughly 4–5 minutes per day → very safe.
- If the target is a Streamlit Cloud app that shows the “Yes, get this app back up!” button,  
  a plain `curl` may not be enough. In that case ask for the Playwright version.