# Deployment Guide

Your Django application is now configured for deployment! Here is how you can make it public using a free hosting provider like **Render** or **Railway**.

## Prerequisites

- A [GitHub](https://github.com/) account.
- Git installed on your computer.

## Step 1: Push Code to GitHub

1.  Initialize a git repository (if you haven't already):
    ```bash
    git init
    git add .
    git commit -m "Initial commit with backend and deployment config"
    ```
2.  Create a new repository on GitHub.
3.  Push your code:
    ```bash
    git remote add origin <your-github-repo-url>
    git branch -M main
    git push -u origin main
    ```

## Step 2: Deploy on Render (Recommended for Beginners)

1.  Sign up at [render.com](https://render.com/).
2.  Click **New +** -> **Web Service**.
3.  Connect your GitHub repository.
4.  Render will automatically detect the configuration:
    - **Runtime**: Python 3
    - **Build Command**: `pip install -r requirements.txt`
    - **Start Command**: `gunicorn myproject6.wsgi`
5.  **Environment Variables**:
    Scroll down to "Environment Variables" and add:

    - `PYTHON_VERSION`: `3.10.12`
    - `SECRET_KEY`: (Generate a random string)
    - `DEBUG`: `False`
    - `ALLOWED_HOSTS`: `*` (or your specific domain)
    - `DATABASE_URL`: (Render creates this automatically if you add a Postgres database, see below)

6.  **Add a Database**:

    - Go to Dashboard -> **New +** -> **PostgreSQL**.
    - Name it (e.g., `mydb`).
    - Copy the **Internal Database URL**.
    - Go back to your Web Service -> Environment -> Add `DATABASE_URL` with the value you copied.

7.  **Deploy**: Click "Create Web Service".

## Step 3: Create Superuser

Once deployed, use the Render "Shell" or "Connect" feature to run:

```bash
python manage.py migrate
python manage.py createsuperuser
```

This allows you to log in to `/admin` and manage your Portfolio projects.

## Important Notes

- **Static Files**: We configured `WhiteNoise` to serve your CSS/Images efficiently.
- **Security**: `DEBUG=False` ensures error pages don't show sensitive info.
- **Admin Panel**: Access it at `your-app-url.com/admin`.
