# Django Project

A Django project configured for Vercel deployment.

## Setup

1. Create a virtual environment:
```bash
python -m venv venv
```

2. Activate the virtual environment:
```bash
# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the root directory:
```
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1,.vercel.app

# PostgreSQL Database Configuration (optional - falls back to SQLite if not set)
DB_NAME=your_database_name
DB_USER=your_database_user
DB_PASSWORD=your_database_password
DB_HOST=localhost
DB_PORT=5432
```
```
# AWS S3 Configuration (required for production/Vercel)
  USE_S3=TRUE
  AWS_ACCESS_KEY_ID=your-access-key
  AWS_SECRET_ACCESS_KEY=your-secret-key
  AWS_STORAGE_BUCKET_NAME=your-bucket-name
  AWS_S3_REGION_NAME=us-east-1
```

**Note:** If PostgreSQL credentials are not provided, the project will automatically use SQLite for local development.

5. Run migrations:
```bash
python manage.py migrate
```

6. Create a superuser:
```bash
python manage.py createsuperuser
```

7. Run the development server:
```bash
python manage.py runserver
```

## Vercel Deployment

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Deploy:
```bash
vercel
```

3. Set environment variables in Vercel dashboard:
   - `SECRET_KEY`
   - `DEBUG=False`
   - `ALLOWED_HOSTS=your-domain.vercel.app,.vercel.app`
   - `DB_NAME` (PostgreSQL database name)
   - `DB_USER` (PostgreSQL username)
   - `DB_PASSWORD` (PostgreSQL password)
   - `DB_HOST` (PostgreSQL host - e.g., from Vercel Postgres or external provider)
   - `DB_PORT` (PostgreSQL port, usually 5432)
   - `USE_S3=TRUE`
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `AWS_STORAGE_BUCKET_NAME`
   - `AWS_S3_REGION_NAME` (optional, defaults to us-east-1)

**Note:** For Vercel, you can use Vercel Postgres or connect to an external PostgreSQL database. Make sure to set all database environment variables for production.

## Project Structure

```
.
├── config/              # Main project configuration
│   ├── __init__.py
│   ├── settings.py      # Django settings
│   ├── urls.py          # Main URL configuration
│   ├── wsgi.py          # WSGI configuration
│   └── asgi.py          # ASGI configuration
├── manage.py            # Django management script
├── requirements.txt     # Python dependencies
├── vercel.json          # Vercel configuration
├── vercel_handler.py    # Vercel serverless handler
└── .gitignore          # Git ignore file
```

