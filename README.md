# Pharmacy Management System 💊

[![Project Status](https://img.shields.io/badge/status-active-brightgreen.svg)](https://github.com/AhmedElkomi/Pharmacy-Management-System)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Issues](https://img.shields.io/github/issues/AhmedElkomi/Pharmacy-Management-System)](https://github.com/AhmedElkomi/Pharmacy-Management-System/issues)

Short, polished description
A robust, database-first Pharmacy Management System designed to centralize medication inventory, customer records, prescriptions, and sales. The system helps pharmacists make data-driven decisions, improves patient safety by flagging potential drug interactions, and streamlines everyday pharmacy workflows.

---

Table of Contents
- [Why this project](#why-this-project)
- [Key Features](#key-features)
- [Architecture & Data Model](#architecture--data-model)
- [Quick Start](#quick-start)
- [Typical Workflows & Examples](#typical-workflows--examples)
- [Tech Stack](#tech-stack)
- [Testing & Quality](#testing--quality)
- [Contributing](#contributing)
- [Roadmap](#roadmap)
- [License & Contact](#license--contact)

Why this project
Pharmacies need reliable systems to manage inventory, process prescriptions, ensure patient safety, and track sales. This project concentrates on the database and core logic enabling:
- Accurate inventory tracking and reorder automation
- Prescription history and customer profiles
- Automated drug interaction checking to reduce adverse events
- Traceable sales and order records for auditing and reporting

Key Features
- Centralized database for medications, customers, prescriptions, sales, and orders
- Inventory status, low-stock alerts, and reorder suggestions
- Patient profiles and prescription history
- Drug interaction checking and safety flags
- Transactional sales records for accurate accounting
- Designed to integrate with a backend API or UI

Architecture & Data Model
This project is focused on the database layer. Typical entities include:
- Medication (id, name, brand, dosage_form, strength, manufacturer, unit_price, current_stock, reorder_level)
- Customer/Patient (id, full_name, dob, phone, email, address, notes)
- Prescription (id, customer_id, prescriber, date_issued, valid_until, instructions)
- PrescriptionItem (id, prescription_id, medication_id, quantity, dosage, frequency, duration)
- Sale (id, sale_date, customer_id, total_amount, payment_method)
- SaleItem (id, sale_id, medication_id, quantity, unit_price, discount)
- Supplier / PurchaseOrder for restocking
- InteractionRules / DrugInteractions table to record known problematic combinations

Simple ER (illustrative)
[Customer] 1---* [Prescription] *---* [Medication]
[Sale] 1---* [SaleItem] *---1 [Medication]

Example ER (ASCII)
+------------+       +-------------+       +-----------+
| Customer   |1 --- *| Prescription|* --- *| Medication|
+------------+       +-------------+       +-----------+
       \                                     /
        \                                   /
         \                                 /
          \--* [Sale] 1 --- * [SaleItem] --/

Database Constraints & Safety
- Use transactions for sales and inventory updates to avoid race conditions.
- Enforce foreign keys and sensible ON DELETE behavior to keep history intact.
- Add indexes on frequently searched columns (medication name, customer phone).

Quick Start
(Adjust commands for your environment — this is a template to get started)

Prerequisites
- PostgreSQL or MySQL (or any SQL RDBMS)
- Optional: Node.js / Python if you plan to run a backend service
- git

Clone
git clone https://github.com/AhmedElkomi/Pharmacy-Management-System.git
cd Pharmacy-Management-System

Database setup (example using psql / PostgreSQL)
- Create database:
  createdb pharmacy_db
- Run migration / schema SQL (replace with actual SQL file names in repo):
  psql -d pharmacy_db -f sql/schema.sql
- (Optional) Seed sample data:
  psql -d pharmacy_db -f sql/seeds.sql

Common commands
- Run migrations: ./scripts/migrate.sh (or use your migration tool: Flyway / Liquibase / knex / alembic)
- Start backend (example): npm install && npm start
- Run tests: npm test (or pytest)

Typical Workflows & Examples
- Record a sale: create Sale + SaleItems, decrement Medication.current_stock inside a transaction.
- Reorder flow: find medications where current_stock <= reorder_level; create PurchaseOrder.
- Check drug interactions: given a customer's current medications + new prescription, search DrugInteractions table and flag matches.

Sample SQL snippets
Get low-stock items:
SELECT id, name, current_stock, reorder_level
FROM Medication
WHERE current_stock <= reorder_level
ORDER BY current_stock ASC;

Find patient prescription history:
SELECT p.id, p.date_issued, pi.medication_id, m.name, pi.quantity
FROM Prescription p
JOIN PrescriptionItem pi ON pi.prescription_id = p.id
JOIN Medication m ON m.id = pi.medication_id
WHERE p.customer_id = 123
ORDER BY p.date_issued DESC;

Tech Stack (suggested)
- Database: PostgreSQL or MySQL
- Backend (optional): Node.js + Express, or Python + Flask/Django
- Migrations: knex / TypeORM / Alembic / Flyway
- Testing: Jest / Mocha or pytest
- Deployment: Docker + container orchestration (optional)

Testing & Quality
- Unit tests for business rules (inventory changes, interaction checks)
- Integration tests for DB migrations and core transactions
- Add CI checks (GitHub Actions) to run migrations, lint, and tests on PRs

Contributing
Contributions welcome! Suggested workflow:
1. Fork the repository
2. Create a feature branch (git checkout -b feat/short-description)
3. Add tests and documentation for your change
4. Open a PR describing the change and why it helps

Please follow conventional commits and keep PRs focused & small.

Roadmap (example ideas)
- Add role-based access control (pharmacist, manager, cashier)
- UI dashboard for inventory, sales, and alerts
- Integrate a third-party drug interaction API for up-to-date interactions
- Reporting module for sales, profitability, and inventory aging
- Mobile-friendly dispensing interface for point-of-sale

License & Contact
This project is available under the MIT License. See LICENSE for details.

Author
Ahmed Elkomi — https://github.com/AhmedElkomi

Acknowledgements
- Thanks to open-source tooling and database design patterns that inspired this project.

If you want, I can:
- tailor this README to the exact tech stack used in your repo,
- generate SQL schema docs from your schema files,
- add GitHub Actions CI examples or a Dockerfile to containerize the app.
