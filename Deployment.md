# Streamlit Cloud Deployment Guide

This guide provides step-by-step instructions for deploying the CircularIQ application to Streamlit Cloud. Following these steps will help you resolve common issues like the `KeyError` related to missing secrets.

## 1. Pre-deployment Checklist

Before deploying, ensure you have the following:

- A GitHub account.
- The application code pushed to a GitHub repository.
- A Streamlit Cloud account.
- Google OAuth credentials (`client_id`, `client_secret`).

## 2. Google OAuth Configuration

Your application uses Google for authentication. You must configure the OAuth consent screen and credentials in the Google Cloud Console.

1.  **Go to the [Google Cloud Console](https://console.cloud.google.com/).**
2.  Navigate to **APIs & Services -> Credentials**.
3.  Find your OAuth 2.0 Client ID.
4.  Under **Authorized redirect URIs**, add the URL of your deployed Streamlit application. The format is typically `https://your-app-name.streamlit.app/`. Streamlit provides the app URL after the first deployment. You may need to deploy once, get the URL, and then add it here.

## 3. Setting Up Secrets

The application requires API keys and credentials to run. You must set these as "secrets" in your Streamlit Cloud app settings.

1.  **Go to your app's page on Streamlit Cloud.**
2.  Click on **"Manage app"** in the lower right corner.
3.  Navigate to the **"Secrets"** management section.
4.  Add the following secrets:

    -   **`hf_token`**: Your Hugging Face API token.
    -   **`client_id`**: Your Google OAuth Client ID.
    -   **`client_secret`**: Your Google OAuth Client Secret.
    -   **`redirect_uri`**: The redirect URI for your Streamlit app (must match the one in the Google Cloud Console).

    *Example*:
    ```toml
    hf_token = "hf_..."
    client_id = "....apps.googleusercontent.com"
    client_secret = "GOCSPX-..."
    redirect_uri = "https://your-app-name.streamlit.app/"
    ```

## 4. Handling Dependencies

Streamlit Cloud automatically installs dependencies from your `requirements.txt` file.

-   **Standard Packages**: All packages listed in `requirements.txt` will be installed via `pip`.
-   **Local Packages**: The `./Chat_input_widget-master` is a local package. Ensure that this directory is correctly pushed to your GitHub repository. Streamlit's dependency management will automatically install it.

## 5. Including the `pdf_files` Directory

The application requires PDF files to be present in the `pdf_files` directory.

-   **Ensure the directory is tracked by Git**: Make sure you have committed the `pdf_files` directory and its contents to your GitHub repository. If the directory is listed in your `.gitignore` file, you will need to remove it from there.

## 6. Deployment Steps

1.  **Log in to Streamlit Cloud.**
2.  Click **"New app"** and select your repository, branch, and main file (`streamlit_app.py`).
3.  Deploy the app.
4.  Once deployed, immediately go to the app's settings and add the secrets as described in section 3.
5.  Ensure your Google Cloud Console has the correct redirect URI for the deployed app.
6.  Reboot the app if necessary for the secrets to be applied.

By following these steps, you should be able to deploy your application successfully.
