# Vault Secure — Full Stack Banking App

## Project Structure
```
vault-secure/
├── index.html          ← Frontend (single file, open in browser)
└── backend/            ← Your Node.js/Express/Prisma backend
    ├── src/
    ├── prisma/
    ├── package.json
    └── .env.example
```

---

## 🚀 Quick Start

### 1. Set up the Backend

```bash
cd backend
npm install
```

Copy and configure your environment:
```bash
cp .env.example .env
```

Edit `.env` with your real values:
```env
PORT=3000
DATABASE_URL="postgresql://user:password@localhost:5432/vault_secure_db"
JWT_SECRET=your_super_secret_key_here_min_32_chars
JWT_REFRESH_SECRET=another_secret_key_here
FRONTEND_URL=http://localhost:3001
```

### 2. Set up the Database

Make sure PostgreSQL is running, then:
```bash
npx prisma migrate dev --name init
npx prisma generate
node prisma/seed.js   # optional: seed demo data
```

### 3. Start the Backend

```bash
npm run dev
# OR
node src/server.js
```

Backend runs at: **http://localhost:3000**
Health check: **http://localhost:3000/health**

### 4. Open the Frontend

Simply open `index.html` in your browser.
No build step needed — it is a single HTML file.

If you hit CORS issues, serve it with:
```bash
npx serve . -p 3001
```
Then open http://localhost:3001

---

## API Endpoints Used

| Feature | Endpoint |
|---|---|
| Register | POST /api/v1/auth/register |
| Login | POST /api/v1/auth/login |
| Profile | GET /api/v1/auth/profile |
| Accounts | GET /api/v1/accounts |
| Balance Summary | GET /api/v1/accounts/summary |
| Transactions | GET /api/v1/transactions |
| Transfer | POST /api/v1/transfers |
| Transfer History | GET /api/v1/transfers |
| Savings Goals | GET/POST /api/v1/savings |
| Fund Goal | POST /api/v1/savings/:id/fund |
| Notifications | GET /api/v1/notifications |
| Change Password | PUT /api/v1/auth/change-password |

---

## Frontend Features

- Landing page with hero, features bento, stats, testimonials, pricing
- Register and Login wired to the backend auth endpoints
- 2FA support — shows TOTP input when server requires it
- Dashboard overview with live balance, recent transactions, goals
- Accounts — list all accounts, open new ones
- Transactions — full history with account and type filters
- Transfers — instant and scheduled transfers
- Savings Goals — create, track, and fund goals
- Notifications — view, mark read, mark all read
- Profile — update personal info, change password

---

## To Change the API URL

Open index.html and find near the top of the script section:
```js
const API = 'http://localhost:3000/api/v1';
```
Change it to your production API URL when deploying.
