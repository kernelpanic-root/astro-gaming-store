# Astro Gaming Store: Web-Based Inventory Management System

A full-stack web application that lets a retail video game store manage its inventory and review sales. Built as a team project for CIS 5800 (Spring 2026).

**Live demo:** https://astro-gaming-store-dmef.onrender.com
*(Hosted on Render's free tier, so the first load after a period of inactivity can take up to a minute.)*

<img width="1453" height="855" alt="admin_dashboard" src="https://github.com/user-attachments/assets/b91f78f5-ea68-4978-9f9c-ef273bab3c40" />


## Features

| Screen    | Features                                                                 |
| --------- | ------------------------------------------------------------------------ |
| Login     | Role-based authentication (Admin / Cashier), bcrypt-hashed passwords     |
| Dashboard | Key metric cards, recent sales feed, stock alert panel, light/dark mode  |
| Inventory | 41 products with search, platform/genre/status filters, pagination, CRUD |
| Add/Edit  | Form validation, reorder threshold warning, delete confirmation          |
| Alerts    | Filter tabs (All / Out of Stock / Low Stock), CSV export, reorder buttons |
| Reports   | Daily revenue chart, platform breakdown, top sellers, CSV export         |
| Offline   | Progressive Web App: service worker caching, offline banner, installable |

**Roles**

- **Admin:** full access (add, edit, delete products)
- **Cashier:** read-only access (view inventory, alerts, dashboard, reports)

The demo database is seeded with sample products and sales data for demonstration purposes only.

## Tech Stack

- **Backend:** Python, Flask, Flask-Bcrypt
- **Database:** SQLite (created automatically on first run)
- **Frontend:** HTML, CSS, Bootstrap 5, Chart.js, Jinja2 templates
- **Deployment:** Render
- **Version control:** Git / GitHub

## Screenshots

| Admin inventory (add / edit / delete) | Cashier inventory (read-only) |
| --- | --- |
| <img width="1465" height="849" alt="admin_inventory" src="https://github.com/user-attachments/assets/58de1a81-fea7-4bde-b68e-bd2865ef9bba" /> | <img width="1470" height="852" alt="cashier_inventory" src="https://github.com/user-attachments/assets/992a1436-c9b7-4913-b53d-3831699df72c" />
 |

| Low-stock alerts | Reports and analytics |
| --- | --- |
| <img width="1456" height="849" alt="admin_alerts" src="https://github.com/user-attachments/assets/99b644b4-2c6f-4d3f-bfd1-3dc3151a8b36" /> | <img width="1464" height="850" alt="admin_reports analytics" src="https://github.com/user-attachments/assets/63421d0b-4e2d-4d25-a7cc-b0033a197973" /> |

## Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/kernelpanic-root/astro-gaming-store.git
cd astro-gaming-store
```

### 2. Create a virtual environment

```bash
# macOS / Linux
python3 -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the app

For local development, the end of `app.py` should read:

```python
if __name__ == "__main__":
    init_db()
    app.run(debug=True, port=8000)
```

Then run:

```bash
python app.py       # Windows
python3 app.py      # macOS / Linux
```

Open your browser at **http://localhost:8000**

## Login

Accounts are created when the database is first seeded (see `database.py`). Login credentials are not published in this repository.

To try the live demo, please contact me for demo credentials.

## Project Structure

```
astro-gaming-store/
├── app.py                 Flask routes and application logic
├── database.py            SQLite setup and seed data
├── requirements.txt       Python dependencies
├── static/
│   ├── css/style.css      Custom styles (light and dark mode)
│   └── js/main.js         Theme toggle and JS helpers
└── templates/
    ├── base.html          Master layout (sidebar, top bar)
    ├── login.html         Login screen
    ├── dashboard.html     Dashboard
    ├── inventory.html     Inventory list
    ├── add_edit_item.html Add / edit form
    ├── alerts.html        Low-stock alerts
    └── reports.html       Reports and analytics
```

The SQLite database (`instance/astro.db`) is created automatically on first run.

## What We Learned as Team

- Hash passwords with bcrypt and never store them in plaintext.
- Use parameterized SQL queries instead of string interpolation.
- Service workers need different caching strategies for static assets and dynamic pages.
