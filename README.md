# 💰 Cash Collection Portal

A Streamlit app for Ops Executives to update payment status for customer deliveries in Chennai.

## Features

- **Login** — Secure email & password authentication
- **Update Payment** — Select Delivery Date → Facility → Customer and update payment details
- **View Records** — Filter by date and facility, view summary metrics and download CSV
- **Credit Duration** — Shown only when Payment Mode is set to **Credit**
- **Color-coded table** — Green (Paid), Yellow (Partial/Credit), Red (Pending)

## How It Works

1. Ops Executive logs in with their email and password
2. Selects the **Delivery Date** and **Facility**
3. Chooses a customer from the list (shown as `CustomerID — CustomerName`)
4. Views read-only order details (OrderKg, BilledKg, FulfilledKg, ReturnKg, Invoice Value)
5. Updates **Payment Status**, **Payment Mode**, **Outstanding Amount** and optionally **Credit Duration**
6. Saves — data is updated in `FnV_CashCollection_Chn` table

## Setup

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Configure Secrets

Create a `.env` file in the project root:

```env
DB_HOST=your_host
DB_PORT=your_port
DB_USER=your_user
DB_PASSWORD=your_password
DB_NAME=your_database
```

### 3. Run Locally

```bash
streamlit run app.py
```

### 4. Deploy on Streamlit Cloud

- Connect this GitHub repo on [share.streamlit.io](https://share.streamlit.io)
- Set **Main file path** to `app.py`
- Add secrets under **Settings → Secrets**:

```toml
DB_HOST = "your_host"
DB_PORT = "your_port"
DB_USER = "your_user"
DB_PASSWORD = "your_password"
DB_NAME = "your_database"
```

## Database Table

**`FnV_CashCollection_Chn`** — Pre-populated with delivery order data. The app updates the following columns:

| Column | Description |
|---|---|
| `PaymentStatus` | Paid / Partial / Pending / Credit |
| `PaymentMode` | Cash / UPI / Bank Transfer / Cheque / Credit |
| `OutstandingAmount` | Amount yet to be collected |
| `CreditDuration` | Shown only when PaymentMode = Credit |
