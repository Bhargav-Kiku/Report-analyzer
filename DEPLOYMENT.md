# Deployment Guide

This guide explains how to deploy the **Report Analyzer** Streamlit application to the web.

## Option 1: Streamlit Community Cloud (RECOMMENDED & EASIEST)
Streamlit provides a free and straightforward way to deploy apps directly from GitHub.

1. **Push your code to GitHub.** Ensure your repository is up to date on GitHub.
2. **Go to [Streamlit Community Cloud](https://share.streamlit.io/)** and log in with your GitHub account.
3. Click **New app**.
4. Select the repository, branch (`main`), and main file path (`src/main.py`).
5. **Set Environment Variables**:
   - Before deploying, click on **Advanced settings**.
   - Under the **Secrets** section, copy the contents of your `.streamlit/secrets.toml` file or format it like this:
     ```toml
     SUPABASE_URL = "your_supabase_url"
     SUPABASE_KEY = "your_supabase_anon_key"
     GROQ_API_KEY = "your_groq_api_key"
     ```
6. Click **Deploy!** The app will build and go live.

## Option 2: Render.com (Docker/PaaS)
We've included a `Dockerfile` and `render.yaml` for automated deployment on Render.

1. **Push your code to GitHub.**
2. **Go to [Render Dashboard](https://dashboard.render.com/)** and log in.
3. **Create a Blueprint Draft**:
   - Click **New** -> **Blueprint**.
   - Connect your GitHub repository.
   - Render will automatically detect the `render.yaml` configuration.
4. **Set Environment Variables**:
   - Render will prompt you for the required environment variables (`SUPABASE_URL`, `SUPABASE_KEY`, `GROQ_API_KEY`). Provide them as secure environment variables.
5. **Deploy**:
   - Click **Apply** or let it build. Once the image is built and deployed, Render will give you a public URL.

## Option 3: VPS / Custom Docker Deployment
If you own a server (like EC2, DigitalOcean, or an on-premise machine):

1. **Pull your code** onto the server.
2. **Build the Docker container:**
   ```bash
   docker build -t report-analyzer .
   ```
3. **Run the container**, passing the secrets as environment variables:
   ```bash
   docker run -p 8501:8501 \
     -e SUPABASE_URL="your_supabase_url" \
     -e SUPABASE_KEY="your_supabase_anon_key" \
     -e GROQ_API_KEY="your_groq_api_key" \
     report-analyzer
   ```
4. Access the app on your server's IP address at port `8501`.
