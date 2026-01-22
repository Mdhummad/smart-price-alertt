🚀 Smart Price Alert

Smart Price Alert is a full-stack web application that helps users track product prices across e-commerce websites and receive alerts when prices drop.
It’s built with modern web technologies and designed to handle dynamic, JavaScript-heavy sites reliably.

✨ What This App Does

Track prices of products from major e-commerce websites

Automatically check prices every day

Maintain complete price history for each product

Notify users via email when prices go down

Secure user accounts with Google authentication

This project focuses on real-world reliability, not just scraping static pages.

🔑 Key Features

🌐 Multi-site Support
Works across different e-commerce platforms without writing site-specific scrapers.

🔐 Google Login
Secure authentication using Google OAuth.

📉 Price History Tracking
Visual charts showing how prices change over time.

⏱ Automated Price Checks
Daily background jobs verify prices automatically.

📬 Email Notifications
Instant alerts when a product becomes cheaper.

🧱 Tech Stack
Frontend

Next.js (App Router)

Tailwind CSS

shadcn/ui

Recharts (for price graphs)

Backend & Services

Supabase

PostgreSQL database

Authentication (Google OAuth)

Row Level Security (RLS)

Scheduled jobs using pg_cron

Firecrawl

JavaScript rendering

Anti-bot handling

AI-based structured data extraction

Resend

Transactional email delivery

🧠 Why Firecrawl?

Most e-commerce websites load prices dynamically and block bots.
Firecrawl handles:

JavaScript-rendered content

Anti-scraping protection

Rotating proxies

AI-driven extraction prompts

This allows the same scraping logic to work across many websites.

📁 Project Structure
smart-price-alert/
├── app/
│   ├── page.js                  # Main landing page
│   ├── actions.js               # Server actions
│   ├── auth/callback/route.js   # OAuth callback
│   └── api/cron/check-prices/   # Daily price checker
├── components/
│   ├── AddProductForm.js
│   ├── ProductCard.js
│   ├── PriceChart.js
│   └── AuthModal.js
├── lib/
│   ├── firecrawl.js             # Firecrawl integration
│   ├── email.js                 # Email templates
│   └── utils.js
├── utils/supabase/
│   ├── client.js
│   ├── server.js
│   └── middleware.js
├── supabase/migrations/
│   ├── 001_schema.sql
│   └── 002_setup_cron.sql
├── proxy.ts
├── .env.example
└── README.md

⚙️ Setup Guide
1️⃣ Clone the Repository
git clone https://github.com/Mdhummad/smart-price-alert.git
cd smart-price-alert
npm install

2️⃣ Supabase Configuration

Create a new project on Supabase

Run database migrations from supabase/migrations

Enable Google authentication

Copy:

Project URL

Anon key

Service role key

3️⃣ Firecrawl Setup

Create an account at https://firecrawl.dev

Generate an API key from the dashboard

4️⃣ Resend Setup

Create an account at https://resend.com

Generate an API key

(Optional) Verify a custom email domain

5️⃣ Environment Variables

Create a .env.local file:

# Supabase
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

# Firecrawl
FIRECRAWL_API_KEY=

# Resend
RESEND_API_KEY=
RESEND_FROM_EMAIL=onboarding@resend.dev

# Security
CRON_SECRET=

# App
NEXT_PUBLIC_APP_URL=http://localhost:3000


Generate CRON_SECRET:

node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"

6️⃣ Run Locally
npm run dev


Open:
👉 http://localhost:3000

🚀 Deployment

The app is deployment-ready for Vercel.

Steps:

Connect the GitHub repo to Vercel

Add environment variables in Vercel dashboard

Update Supabase cron function with production URL

Add production redirect URL in Google OAuth settings

🔄 How Automation Works

Supabase pg_cron runs daily

Cron triggers /api/cron/check-prices

Firecrawl fetches latest prices

Database updates price history

Email sent if price drops

All secured using a secret token.

🧪 Testing Cron Endpoint
curl -X POST https://your-app.vercel.app/api/cron/check-prices \
  -H "Authorization: Bearer YOUR_CRON_SECRET"

🛠 Common Issues

Google login fails → Check redirect URIs

Cron not running → Verify pg_cron & secret

Emails not sending → Check Resend logs

Scraping errors → Review Firecrawl dashboard

🌱 Future Improvements

Price prediction using ML

Telegram / WhatsApp alerts

Browser extension

Product comparison dashboard

👤 Author

Mohammed Hammad
Built as a real-world full-stack project to demonstrate scalable scraping, automation, and authentication.
