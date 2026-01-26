# Streamlit Cloud Deployment Guide

This guide provides step-by-step instructions for deploying the CircularIQ application to Streamlit Cloud. Following these steps will help you resolve common issues like the `KeyError` related to missing secrets.

## 1. Pre-deployment Checklist

Before deploying, ensure you have the following:

- A GitHub account.
- The application code pushed to a GitHub repository.
- A Streamlit Cloud account.

## 2. Setting Up Secrets

The `KeyError` you encountered is because the application requires API keys that are not part of the code. You must set these as "secrets" in your Streamlit Cloud app settings.

1.  **Go to your app's page on Streamlit Cloud.**
2.  Click on **"Manage app"** in the lower right corner.
3.  Navigate to the **"Secrets"** management section.
4.  Add the following secrets:

    -   **`azure_api_key`**: Your Azure OpenAI API key.
    -   **`hf_token`**: Your Hugging Face API token.

    *Example*:
    ```toml
    azure_api_key = "your_azure_api_key_here"
    hf_token = "your_hugging_face_token_here"
    ```

## 3. Handling Dependencies

Streamlit Cloud automatically installs dependencies from your `requirements.txt` file.

-   **Standard Packages**: All packages listed in `requirements.txt` will be installed via `pip`.
-   **Local Packages**: The `./Chat_input_widget-master` is a local package. Ensure that this directory is correctly pushed to your GitHub repository. Streamlit's dependency management will automatically install it.

## 4. Including the `pdf_files` Directory

The application requires PDF files to be present in the `pdf_files` directory.

-   **Ensure the directory is tracked by Git**: Make sure you have committed the `pdf_files` directory and its contents to your GitHub repository. If the directory is listed in your `.gitignore` file, you will need to remove it from there.

## 5. Deployment Steps

1.  **Log in to Streamlit Cloud.**
2.  Click **"New app"** and select your repository, branch, and main file (`streamlit_app.py`).
3.  Deploy the app.
4.  Once deployed, immediately go to the app's settings and add the secrets as described in section 2.
5.  Reboot the app if necessary for the secrets to be applied.

By following these steps, you should be able to deploy your application successfully and resolve the `KeyError`.
