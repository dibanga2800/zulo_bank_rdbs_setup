# 🏦 Zulo Bank RDBS Setup

**Zulo Bank RDBS Setup** is a Python-based project that automates the creation and initialization of a PostgreSQL relational database for Zulo Bank. It handles schema creation, table definitions, and ensures a clean, consistent setup environment—ideal for development, testing, or demonstration purposes.
---

## 📁 Project Structure

├── .env # Environment variables containing database credentials
├── create_db.py # Script: connect to Postgres, create the Zulo Bank database if not exists
├── create_tables.py # Script: connect to the Zulo Bank database and build schemas/tables
├── requirements.txt # Python dependencies (e.g. psycopg2, python-dotenv)
└── README.md # Project overview and setup instructions


---

## ⚙️ Features

- ✅ **Environment-based configuration** — Load DB connection details from `.env`
- 🗄️ **Automated database creation** — Creates the database if it doesn’t exist
- 📊 **Schema and table builder** — Defines `zulobankdb` schema with transactional tables
- 🧪 **Idempotent operations** — Safe to rerun without duplicating DTOs or schemas

---

## 🔧 Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/dibanga2800/zulo_bank_rdbs_setup.git
cd zulo_bank_rdbs_setup

2. Install dependencies
pip install -r requirements.txt

3. Create .env file
DB_USERNAME=<your_postgres_user>
DB_PASSWORD=<your_postgres_password>
DB_HOST=127.0.0.1
DB_PORT=5432
DB_NAME=zulobank

🚀 Usage
python create_db.py

4. Create the database
python create_db.py


5. Build the schema and tables
python create_tables.py

📦 Table Schema Overview
| Table Name        | Primary Key      | Key Columns & FKs                                                 |
| ----------------- | ---------------- | ----------------------------------------------------------------- |
| `date_dim`        | `date_id`        | `Year`, `Month`, `Day`                                            |
| `transaction`     | `Transaction_id` | `TransactionType`, `Amount`, FK → `date_dim.date_id`              |
| `accounts`        | `Account_id`     | `AccountType`, `Balance`, FK → `date_dim.date_id`                 |
| `loans`           | `Loan_id`        | `LoanType`, `LoanAmount`, `InterestRate`, FK → `date_dim.date_id` |
| `customers`       | `Customer_id`    | Personal contact information                                      |
| `zulo_fact_table` | (composite FKs)  | Links customer/account/transaction/loan IDs into a fact table     |


🛠 Troubleshooting
psycopg2.OperationalError: Ensure PostgreSQL is running & listening on 127.0.0.1:5432

Connection hangs or no output: Confirm .env credentials are set and loaded

Empty schema or missing tables: Look for “empty query” errors → ensure create_tables.py is being executed correctly

🔁 Next Steps & Roadmap
 Seed tables with sample data (customers, accounts, transactions)

 Write ETL or API integration scripts

 Add unit tests using pytest and CI/CD pipelines

 Generate ER diagrams and visualize relationships

 Containerize with Docker and orchestration via Docker Compose

📧 Contributing
Contributions are very welcome! Feel free to:

Open issues for bugs or improvement suggestions

Submit pull requests for new features or fixes

Update this README for clarity, additional usage demos, or tips

📝 License & Credits
This project was bootstrapped for educational/demonstration use.
Feel free to use or remix under the MIT License.


Zulo Bank RDBS Setup · by David Ibanga · Jul 2025

---
Let me know if you'd like a `LICENSE` file generated as well, or if you're planning to add Docker or testing support—I can scaffold that too.






