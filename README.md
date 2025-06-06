
# 🛍️ LiebeMama – B2B Product Management Platform

**LiebeMama** is a production-grade, multilingual platform built with Flask for managing and showcasing products (e.g., halawa and tahini) for B2B clients, especially restaurants. It provides a complete system for merchants and administrators to handle product uploads, approvals, notifications, and image storage using MinIO.

---

## 🚀 Live Version

> 🌐 Hosted on Hetzner Cloud  
> 🔐 Protected via Cloudflare  
> 🛡️ HTTPS Enabled (Let's Encrypt)  
> 🧩 WSGI Server: Gunicorn + Nginx Reverse Proxy

---

## 📦 Features

- ✅ Admin & Merchant dashboards with role-based access
- 🖼️ Secure image upload (MinIO) with multi-image support
- 🔔 Dynamic notification system between roles
- 🧠 Product AI analysis endpoint (stub ready)
- 🛠️ Tools for DB reset, translation, logging
- 🌐 Multilingual (Arabic, German) with auto-translation
- 📜 Markdown-based developer documentation
- 📁 Scalable codebase using Flask Blueprints

---

## 🧱 Project Structure (Simplified)

```
liebemama/
├── routes/              # Admin, Merchant, Auth, Products, Images, Notifications
├── models/              # SQLAlchemy models
├── logic/               # Helpers: validation, logging, notifications
├── static/              # CSS, JS, uploads
├── templates/           # Jinja2 views
├── config/              # Logging config
├── translations/        # i18n files (.po/.mo)
├── myapp.py             # Main app entry point
├── wsgi.py              # WSGI entry for Gunicorn
├── requirements.txt
├── .env.example
```

---

## 🔧 Setup & Installation

### 1. Clone & Install

```bash
git clone https://github.com/TamerOnLine/liebemama.git
cd liebemama
pip install -r requirements.txt
```

### 2. Create `.env`

```
SECRET_KEY=your-secret-key
DATABASE_URL=postgresql://user:pass@localhost/dbname
MINIO_ENDPOINT=your-minio-url
MINIO_ACCESS_KEY=your-key
MINIO_SECRET_KEY=your-secret
MINIO_BASE_URL=https://files.liebemama.com/
MINIO_BUCKET_ADMIN=admin-product
MINIO_BUCKET_MERCHANT=merchant-product
SITE_NAME=LiebeMama
```

### 3. Initialize DB (optional)

```bash
python restart.py  # Choose option 2 to create tables safely
```

### 4. Run Locally

```bash
python myapp.py
```

Or with Gunicorn:

```bash
gunicorn -w 4 -b 0.0.0.0:8030 wsgi:app
```

---

## 🌍 Internationalization (i18n)

- Translations handled via `flask-babel` and `deep-translator`
- To update translation files:

```bash
python i18n.py
```

---

## 🧪 Dev Tools & Scripts

| Script | Purpose |
|--------|---------|
| `restart.py` | Drop or create tables |
| `delet.py` | Delete a specific table interactively |
| `i18n.py` | Auto-translate interface |
| `myapp.py` | Launch app and seed Super Admin |
| `wsgi.py` | Production entry for Gunicorn |

---

## 🛡️ Security

- Auth via `Flask-Login`
- RBAC via decorators (`admin_only`, `merchant_required`)
- Form validation using Cerberus + Bleach
- Error logging in DB + file-based logs (`logs/error.log`)
- Protected image deletion and upload by owner

---

## 🧠 Developer Notes

- Code is modular and highly maintainable
- Notifications are dynamic and task-oriented
- Support for future extension: orders, invoices, statistics
- Supports Cloudinary fallback (not default)

---

## 🔀 Branch Strategy

The project uses Git branches to separate environments and development tasks.

### 📌 Main Branches

- `main`: Stable production-ready code.
- `dev`: Ongoing development, testing new features before merging to `main`.

### 🌱 Feature Branches

Developers can use custom feature branches such as:

- `docs-update` – for documentation updates
- `auth-refactor` – for rewriting authentication logic
- `admin-ui-enhance` – for UI improvements on admin side

### 🧩 Switch Between Branches

To switch to an existing branch:

```bash
git checkout dev
```

To create a new feature branch:

```bash
git checkout -b your-feature-name
```

Push the new branch to GitHub:

```bash
git push origin your-feature-name
```

---

## ✍️ Author

**Tamer Hamad Faour**  
[GitHub](https://github.com/TamerOnLine) • [LinkedIn](https://www.linkedin.com/in/tameronline/) • [YouTube: Tamer On Pi](https://www.youtube.com/@mystrotamer)

---

## 📄 License

Licensed under the [Apache License, Version 2.0](./LICENSE).  
You may obtain a copy of the License in the project root.

---
