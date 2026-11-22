# Royal Home Services

A full-stack Django website for Royal Home Services, providing cleaning service information, online appointment bookings, employee registrations, customer complaints, customer reviews, and a protected staff dashboard.

**Repository:** https://github.com/mrabidullah/royalhomeservices  
**Primary service areas:** Rawalpindi and Islamabad, Pakistan

## Features

### Public website
- Responsive home page with cleaning service listings
- Service/category detail pages
- Online appointment and quote request form
- Employee registration form
- Customer complaint submission form
- About page
- Approved customer reviews
- WhatsApp and social contact links
- SEO titles, descriptions, canonicals, Open Graph metadata, JSON-LD, sitemap, and robots configuration

### Staff dashboard
- Staff-only authentication with login throttling and secure sessions
- Order/booking management
- Employee registration management
- Complaint management and complaint detail views
- Customer review approval
- Location and date filtering, search, pagination, and delete actions
- Rawalpindi, Islamabad, and Other location classifications

## Technology stack

- Python 3
- Django 5.2
- SQLite
- Tailwind CSS 4
- Pillow for Django image fields
- HTML, CSS, JavaScript

## Application structure

| Path | Purpose |
|---|---|
| `homepage/` | Home page, bookings, categories, services, SEO, and sitemaps |
| `employes/` | Employee registration |
| `complaint/` | Complaints and About page |
| `admin2/` | Staff authentication and dashboard |
| `config/` | Django settings, ASGI/WSGI configuration, and main routes |
| `templates/` | Django templates |
| `static/` | Compiled Tailwind CSS, images, and public assets |
| `media/` | Uploaded service images |

## Public routes

| Route | Description |
|---|---|
| `/` | Home page |
| `/about/` | About Royal Home Services |
| `/complaint/` | Customer complaint form |
| `/employe/` | Employee registration |
| `/review/` | Customer review submission |
| `/explor_views/<slug>/` | Service category page |
| `/robots.txt` | Search engine crawler rules |
| `/sitemap.xml` | XML sitemap |

## Staff routes

| Route | Description |
|---|---|
| `/adminlogin/` | Staff login |
| `/dashboard/orders/` | Booking list |
| `/dashboard/employees/` | Employee registrations |
| `/dashboard/complaints/` | Customer complaints |
| `/dashboard/reviews/` | Customer review moderation |
| `/admin/` | Django administration |

## Local development

### 1. Clone the repository

```powershell
git clone https://github.com/mrabidullah/royalhomeservices.git
cd royalhomeservices
```

### 2. Create and activate a virtual environment

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3. Install Python dependencies

```powershell
python -m pip install --upgrade pip
python -m pip install "Django>=5.2,<5.3" Pillow
```

### 4. Apply database migrations

```powershell
python manage.py migrate
```

The project uses SQLite and stores the database in `db.sqlite3`.

### 5. Create a staff account

```powershell
python manage.py createsuperuser
```

The new account must have **Staff status** enabled to access the custom dashboard.

### 6. Compile Tailwind CSS

Install Node.js dependencies:

```powershell
npm install
npm run tailwind:build
```

During template development, keep the Tailwind watcher running:

```powershell
npm run tailwind:watch
```

### 7. Start the development server

```powershell
python manage.py runserver
```

Open http://127.0.0.1:8000/

## Environment variables

The following environment variables are supported in production:

| Variable | Purpose |
|---|---|
| `DJANGO_SECRET_KEY` | Django secret key; use a long random value in production |
| `DJANGO_DEBUG` | Set to `0` to disable debug mode |
| `DJANGO_ALLOWED_HOSTS` | Comma-separated allowed hosts |
| `SITE_URL` | Preferred public origin, for example `https://www.example.com` |

PowerShell example:

```powershell
$env:DJANGO_SECRET_KEY = "replace-with-a-long-random-secret"
$env:DJANGO_DEBUG = "0"
$env:DJANGO_ALLOWED_HOSTS = "www.example.com,example.com"
$env:SITE_URL = "https://www.example.com"
python manage.py runserver
```

Use the exact public origin in `SITE_URL`, without a trailing slash. `DJANGO_ALLOWED_HOSTS` is required when debug mode is disabled.

## Tests

Run the complete Django test suite:

```powershell
python manage.py test
```

Run Django system checks:

```powershell
python manage.py check
python manage.py makemigrations --check --dry-run
```

The dashboard and public-site regression tests cover authentication, staff permissions, booking submissions, employee registrations, complaints, reviews, SEO metadata, sitemap/robots behavior, and canonical host redirects.

## Production checklist

Before deploying:

1. Set `DJANGO_SECRET_KEY` to a strong unique value.
2. Set `DJANGO_DEBUG=0`.
3. Configure `DJANGO_ALLOWED_HOSTS`.
4. Configure `SITE_URL` to the real public website origin.
5. Use HTTPS and configure proxy/TLS settings when applicable.
6. Run migrations against the production database.
7. Compile Tailwind CSS and serve Django static/media files through your hosting stack.
8. Back up `db.sqlite3` before migrations or database changes.
9. Create or authorize a staff account for the custom dashboard.

If your hosting provider expects an application entry point, Django's WSGI and ASGI modules are:

- `config.wsgi.application`
- `config.asgi.application`

## Admin access

- Django admin: `/admin/`
- Custom staff dashboard: `/adminlogin/`

Custom dashboard access is limited to active users with staff or superuser status. Login attempts are throttled per IP address and username.

## Contact

- Phone / WhatsApp: +92 305 3000854
- Email: khan07861122330@gmail.com
- Facebook: https://www.facebook.com/share/1FQxapvaFA/
- Instagram: https://www.instagram.com/ibrahim50354

## License

No license has been specified for this repository. All rights remain with the project owner unless an applicable license is added.
