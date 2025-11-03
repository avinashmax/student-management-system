# 🎓 Student Management System  
[![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python)](https://www.python.org/)
[![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?logo=mysql)](https://www.mysql.com/)
[![Tkinter](https://img.shields.io/badge/Tkinter-GUI-ffb703)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> 💡 A beginner-friendly project to manage students’ data using **Python GUI (Tkinter)** and **MySQL Database**.  
> Includes features like Add, Update, Delete, and Search with a clean UI.

# 🎓 Student Management System (AWS RDS + MySQL)

This is a **Python-based Student Management System** that connects to an **AWS RDS MySQL database**.  
It allows you to create, view, update, and delete student data tables — all from the terminal using simple menu options.

This project demonstrates how a **real-world database management tool** works, using:
- `mysql-connector-python`
- `dotenv` for secure credential management
- AWS RDS (or any MySQL instance)

---

## 📁 Project Structure

```
student-management/
│
├── main.py               # Main program (menu + CRUD operations)
├── db_connect.py         # Handles AWS RDS connection setup
├── db_config.py          # Optional: used if modular configuration is needed
├── .env                  # Environment file (stores your DB credentials)
├── requirements.txt      # Required Python dependencies
└── README.md             # Project documentation (this file)
```

---

## ⚙️ Setup Instructions

Follow these steps carefully before running the project.

### 1. 🐍 Create and Activate a Virtual Environment

Open your terminal in VS Code and run:

```bash
python -m venv venv
venv\Scripts\activate
```

---

### 2. 📦 Install Dependencies

Install all required Python libraries using:

```bash
pip install -r requirements.txt
```

> The `requirements.txt` file includes:
> ```
> mysql-connector-python==8.0.33
> python-dotenv==1.0.1
> protobuf==3.20.3
> ```

---

### 3. 🔑 Set Up the `.env` File

This file holds your **AWS RDS MySQL connection credentials**.  
It should be placed in the **root folder** of your project.

> ⚠️ Important: `.env` should **never** be pushed to GitHub — it contains sensitive info!

Create a file named `.env` and add your own credentials like this:

```ini
DB_HOST=your-rds-endpoint.ap-south-1.rds.amazonaws.com
DB_USER=your_username
DB_PASSWORD=your_password
DB_NAME=your_database_name
```

✅ Example (for testing locally):
```ini
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=1234
DB_NAME=student_db
```

---

### 4. 🧩 Test the Database Connection

Run this command to verify your `.env` setup:

```bash
python db_connect.py
```

If everything is correct, you’ll see:
```
Connection successful...!
```

If not, recheck:
- RDS is **publicly accessible**
- Your **IP is whitelisted** in the AWS RDS security group
- `.env` values are **correct**

---

## 🚀 Running the Project

After setup, run the main script:

```bash
python main.py
```

### You’ll See a Menu Like This:
```
=== STUDENT MANAGEMENT SYSTEM (AWS RDS + MySQL) ===

Available tables:
1. students

Do you want to (u)se existing or (c)reate new table?
```

---

## 🧱 Features

### 1. Create New Tables
- If no table exists, the program asks:  
  `"No tables found. Do you want to create a new one?"`
- You can define custom columns (e.g., name, age, marks).
- **NOTE:** Every table automatically includes an `id` column (auto-increment primary key).  
  You **don’t need to create it manually**.

Example:
```
Enter column name: name
Select data type: 1. VARCHAR(255)
Enter column name: age
Select data type: 2. INT
Enter column name: marks
Select data type: 3. FLOAT
```

✅ Result:
```
Table 'students' created successfully!
Structure: id (auto), name VARCHAR(255), age INT, marks FLOAT
```

---

### 2. View Records
Displays all records in a clean table format.

```
----------------------------------------
id | name | age | marks
----------------------------------------
1  | Avinash | 22 | 92.0
2  | Sakthi  | 21 | 85.0
----------------------------------------
```

---

### 3. Add Record
Prompts you to enter data for each column (except `id`, which auto-increments).

```
Enter values for the following fields:
name: Dinesh
age: 20
marks: 88
```

---

### 4. Update Record
Lets you update any field (name, age, marks, etc.) for a selected record.

```
Enter ID of record to update: 2
Available columns to update:
- name
- age
- marks
Enter column name to update: marks
Enter new value: 91
Record updated successfully!
```

---

### 5. Delete Record
Deletes a specific record using its `id`, and reorders IDs automatically.

```
Enter ID of record to delete: 3
Record deleted successfully!
```

---

### 6. Delete Table
Safely delete any table from your database.

```
Available tables:
1. students
2. teacher

Enter table number to delete: 2
Are you sure you want to delete 'teacher'? (y/n): y
Table 'teacher' deleted successfully.
```

---

## 🧠 How It Works

- Connects securely to your AWS RDS using `.env` credentials.
- Auto-creates an `id` column for every table.
- Uses `mysql-connector-python` for executing SQL queries.
- Error handling ensures program doesn’t crash even if:
  - Invalid SQL input is given
  - Table already exists
  - Table or record not found

---

## 🧰 Example Commands Recap

```bash
python db_connect.py   # Test AWS connection
python main.py         # Run full Student Management System
```

---

## 🧾 License

This project is open-source and free to use for educational and learning purposes.

---

## 👨‍💻 Author

**Avinash S**  
💼 *Aspiring AWS Cloud Engineer | Python Developer*  
🌐 [GitHub Profile](https://github.com/avinashmax)

