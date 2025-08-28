# Server Deployment Setup

This repository includes a GitHub Action workflow that automatically deploys the Hugo site to your server when code is pushed to the master branch.

## Required GitHub Secrets

To use the deployment workflow, you need to set up the following secrets in your GitHub repository:

1. **SERVER_HOST**: The IP address or hostname of your server
2. **SERVER_USER**: The username for SSH access to your server  
3. **SERVER_PASSWORD**: The password for SSH access to your server

## Setting up GitHub Secrets

1. Go to your repository on GitHub
2. Click on **Settings** tab
3. In the left sidebar, click **Secrets and variables** → **Actions**
4. Click **New repository secret**
5. Add each of the required secrets:
   - Name: `SERVER_HOST`, Value: Your server IP address
   - Name: `SERVER_USER`, Value: Your SSH username
   - Name: `SERVER_PASSWORD`, Value: Your SSH password

## What the Deployment Does

The deployment workflow will:

1. SSH into your server using the provided credentials
2. Navigate to the `jubilant-octo-rotary-phone` directory
3. Switch to the master branch (`git checkout master`)
4. Pull the latest changes (`git pull origin master`)
5. Remove any `draft: true` lines from posts in `content/posts/*.md`
6. Build the site using Hugo (`hugo`)

## Manual Deployment

You can also trigger the deployment manually:

1. Go to the **Actions** tab in your GitHub repository
2. Select **Deploy to Server** workflow
3. Click **Run workflow**
4. Choose the master branch and click **Run workflow**

## Prerequisites on Server

Make sure your server has:
- Git installed and configured
- Hugo installed and available in PATH
- The repository cloned in a directory named `jubilant-octo-rotary-phone`
- SSH access enabled with password authentication