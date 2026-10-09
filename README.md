# Pharmacy Management System 💊

Description
A robust, database-first Pharmacy Management System designed to centralize medication inventory, customer records, prescriptions, and sales. The system helps pharmacists make data-driven decisions, improves patient safety by flagging potential drug interactions, and streamlines everyday pharmacy workflows.

---

Table of Contents
- [Why this project](#why-this-project)
- [Key Features](#key-features)
- [Architecture & Data Model](#architecture--data-model)

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
