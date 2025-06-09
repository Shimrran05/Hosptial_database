# 🏥 Hospital Administrator’s Database Design - ADBMS Project

## 📘 Project Overview
This project is part of our Advanced Database Management Systems (ADBMS) coursework. It involves designing and implementing a comprehensive **Hospital Administrator’s Database** using SQL and relational database principles. The goal is to create a well-structured database system to efficiently manage hospital operations such as patient records, doctor schedules, billing, and departmental activities.

The project was built collaboratively and is hosted on GitHub. It demonstrates skills in SQL scripting, database design, normalization, and procedural programming.

---

## 📁 Data Dictionary
We designed the database using a relational model, and the key entities include:

| Table         | Description                          | Key Columns                          |
|---------------|--------------------------------------|---------------------------------------|
| `Patient`     | Contains patient demographics        | `patient_id`, `name`, `age`, `gender` |
| `Doctor`      | Contains doctor details              | `doctor_id`, `name`, `specialization` |
| `Appointment` | Tracks patient-doctor appointments   | `appointment_id`, `doctor_id`, `patient_id`, `appointment_date` |
| `Department`  | Holds department information         | `dept_id`, `dept_name`                |
| `Bill`        | Tracks patient payments and billing  | `bill_id`, `patient_id`, `amount`, `payment_date` |

---

## 🧱 DDL (Data Definition Language)
All tables were created using SQL DDL commands. Key constraints such as PRIMARY KEY, FOREIGN KEY, and NOT NULL were enforced. Here’s a brief example:

```sql
CREATE TABLE Patient (
    patient_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    gender CHAR(1)
);

CREATE TABLE Appointment (
    appointment_id INT PRIMARY KEY,
    patient_id INT REFERENCES Patient(patient_id),
    doctor_id INT REFERENCES Doctor(doctor_id),
    appointment_date DATE
);
```

All table definitions can be found in the `/ddl/` folder in the GitHub repository.

---

## 📌 SQL Queries (DML)
We wrote SQL queries to perform typical hospital admin tasks. These include:

- Fetching patient histories
- Viewing doctor schedules
- Generating reports for billing
- Departmental doctor count analysis

All queries are available in the `/queries/` folder of the repo.

Example:
```sql
SELECT P.name, A.appointment_date, D.name AS doctor_name
FROM Appointment A
JOIN Patient P ON A.patient_id = P.patient_id
JOIN Doctor D ON A.doctor_id = D.doctor_id;
```

---

## ⚙️ Stored Procedures
We implemented stored procedures for modularity and automation:

- `ScheduleAppointment` – Automates new appointment creation
- `GenerateBill` – Generates billing records with patient ID and payment info

Example:
```sql
CREATE PROCEDURE GenerateBill (
    IN p_id INT,
    IN amt DECIMAL(10,2)
)
BEGIN
    INSERT INTO Bill (patient_id, amount, payment_date)
    VALUES (p_id, amt, CURDATE());
END;
```

Stored procedures are stored in the `/procedures/` folder.

---

## 🗃️ Folder Structure
```
├── ddl/
│   └── create_tables.sql
├── queries/
│   └── all_queries.sql
├── procedures/
│   └── stored_procedures.sql
├── data_dictionary.xlsx
├── ER_Diagram.png
└── README.md
```

---

## 📈 ER Diagram
The ER model visually represents entity relationships such as Patient ↔ Appointment ↔ Doctor and supports normalization up to 3NF. View in docx file 

---

## ✅ Features Implemented
- Relational schema design
- Data dictionary for all entities
- Full DDL creation scripts
- Functional SQL queries for hospital operations
- Modular stored procedures
- Entity Relationship Diagram (ERD)

---

## 💡 Skills Applied
- SQL (DDL, DML, DCL)
- ER Modeling
- Data Normalization (1NF to 3NF)
- Stored Procedures
- Relational Design Best Practices

s
