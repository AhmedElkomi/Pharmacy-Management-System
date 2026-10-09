# 💊 Pharmacy Management System

A Python-based Pharmacy Management System designed to simplify pharmacy operations through a graphical user interface (GUI) and a database-driven architecture. The system helps pharmacy staff manage medicine inventory, customer information, orders, payments, sales, and prescriptions while providing a drug interaction checking feature to support medication safety.

## 📌 Table of Contents

* [Overview](#overview)
* [Features](#features)
* [Technologies Used](#technologies-used)
* [System Modules](#system-modules)
* [Database Management](#database-management)
* [Project Structure](#project-structure)
* [Future Improvements](#future-improvements)
* [Team Members](#team-members)
* [Supervisors](#supervisors)
* [References](#references)

## 📖 Overview

The Pharmacy Management System is a database project developed to improve the efficiency of pharmacy operations and simplify the management of medicine-related information.

The application provides a graphical user interface built with PyQt5, allowing users to interact with the system through dedicated windows and forms. It also includes a drug interaction checker that queries the database to identify potential interactions between two medicines.

By centralizing pharmacy data, the system aims to improve data organization, simplify record management, and support safer medication practices.

## ✨ Features

* **Login System:** Provides a login interface for accessing the application.
* **Medicine Management:** Add and manage medicine information.
* **Customer Management:** Store and manage customer records.
* **Order Management:** Record and manage pharmacy orders.
* **Payment Management:** Store payment-related information.
* **Sales Management:** Record sales transactions.
* **Prescription Management:** Manage prescription records.
* **Drug Interaction Checker:** Check the database for potential interactions between two medicines and display available interaction details and severity.
* **User-Friendly GUI:** Provides an intuitive interface built with PyQt5.
* **Database Integration:** Uses SQL queries to store and retrieve structured information.
* **Error Handling:** Displays success and error messages to help users identify database operation results.

## 🛠️ Technologies Used

| Technology                 | Purpose                                           |
| -------------------------- | ------------------------------------------------- |
| Python                     | Core programming language                         |
| PyQt5                      | Graphical User Interface (GUI)                    |
| SQL                        | Database queries and data management              |
| Database Management System | Structured storage and retrieval of pharmacy data |

*Note: The specific database engine and connection library depend on the project's implementation.*

## 🧩 System Modules

### 1. Login Window

Provides a login form where users enter their username and password before accessing the main application.

### 2. Medicine and Data Management

Provides forms for adding records related to:

* Medicines
* Customers
* Orders
* Payments
* Sales
* Prescriptions

The application executes SQL queries to insert records into the database and provides feedback about successful or failed operations.

### 3. Drug Interaction Checker

Allows users to enter the names of two medicines and check whether an interaction is recorded in the database.

The module retrieves the relevant information and displays the available interaction details and severity. If no matching record is found, the application informs the user.

**Important:** The results depend on the completeness and accuracy of the underlying database. This feature is an informational aid and should not replace professional medical judgment or a comprehensive clinical drug interaction screening system.

## 🗄️ Database Management

The system uses a relational database approach to organize pharmacy-related information and support data retrieval and manipulation through SQL queries.

The database is intended to support records for:

* Medicines and their properties
* Customers
* Orders
* Payments
* Sales transactions
* Prescriptions
* Drug interactions and their severity

The database schema, table relationships, primary keys, foreign keys, and constraints should be documented alongside the actual database implementation.

## 📁 Project Structure

The project includes several application modules responsible for authentication, data management, and drug interaction checking.

```text
Pharmacy-Management-System/
├── README.md
├── requirements.txt          # If included
├── main.py                   # Example entry point; verify filename
├── database/                 # If organized separately
├── assets/                   # Images and GUI resources, if included
└── *.py                      # Application modules
```

*Note: This structure is illustrative. Update the filenames and directories to match the actual repository.*

## 🔮 Future Improvements

Potential enhancements include:

* **Expanded Medicine Information:** Add dosage guidelines, contraindications, side effects, and other clinically relevant information.
* **Inventory Alerts:** Notify users when stock is low or medicines are approaching their expiration dates.
* **Advanced Search and Reporting:** Add filtering, sales reports, and inventory analytics.
* **Mobile Application:** Develop a mobile interface for accessing pharmacy information remotely.
* **Electronic Health Record Integration:** Explore integration with Electronic Health Record (EHR) systems where appropriate.
* **Security Improvements:** Implement secure password hashing, role-based access control, and protected database credentials.
* **Improved Drug Interaction Screening:** Use reliable, maintained clinical data sources and provide appropriate warnings and references.


## 📚 References

1. Xiong, G., Yang, Z., Yi, J., Wang, N., Wang, L., Zhu, H., Wu, C., Lu, A., Chen, X., Liu, S., Hou, T., & Cao, D. (2022). DDInter: An online drug–drug interaction database towards improving clinical decision-making and patient safety. *Nucleic Acids Research*. https://doi.org/10.1093/nar/gkab880

2. Data Base Project on Pharmacy Management System. (n.d.). http://fasteducationlearning.blogspot.com/p/data-base-project-on-pharmacy.html

---

## 📄 Academic Project

This project was developed as part of a database course to demonstrate the application of database management concepts, SQL operations, and graphical user interface development in a practical pharmacy management scenario.

**Disclaimer:** This project is intended for educational purposes. Its drug interaction results depend on the underlying data and should not be considered a substitute for professional clinical decision-making.
