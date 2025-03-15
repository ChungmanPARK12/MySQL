## Logical Backup and Recovery with MySQL Workbench**

### **Logical Backup (Exporting a Database in MySQL Workbench)**
A logical backup saves the **database schema and data** as an SQL file.

### **Step 1: Open MySQL Workbench**
- Launch **MySQL Workbench** and connect to your database.

### **Step 2: Go to Data Export**
- Click **"Server"** in the top menu.
- Select **"Data Export"**.

### **Step 3: Select Database and Tables**
- Choose the database (e.g., `samsdb`).
- Select **"Export to Self-Contained File"**.
- Choose a location to save the backup file (e.g., `samsdb_backup.sql`).

### **Step 4: Start Export**
- Click **"Start Export"**.
- Wait for the process to complete.
- The backup file is now saved.

---

### **Logical Recovery (Importing a Database in MySQL Workbench)**

### **Step 1: Go to Data Import**
- Click **"Server" > "Data Import"**.
- Select **"Import from Self-Contained File"**.
- Choose the backup file (e.g., `samsdb_backup.sql`).

### **Step 2: Start Import**
- Click **"Start Import"**.
- Wait for the process to restore the database.
- Once completed, check if all **tables and data have been restored**.

---

## **Logical Backup and Recovery with Command Prompt**

### **Logical Backup (Using Command Line)**

### **Step 1: Locate MySQL `bin` Directory**
The **MySQL Server 8.0 `bin` directory** contains essential utilities like `mysqldump.exe` for database backups.
- The **backup script (`samsdb_backup.bat`)** is stored in this folder.

---

### **Step 2: Run the Backup Script**
Open **Command Prompt as Administrator** and navigate to the MySQL `bin` folder:
```sh
cd "C:\Program Files\MySQL\MySQL Server 8.0\bin"
```
Then, execute the **backup script**:
```sh
samsdb_backup.bat
```
- **Enter the MySQL password** when prompted.

---

### **Step 3: Verify the Backup File**
After running the script, a new **SQL backup file (`.sql`)** appears in `C:\mysql_backup\`.

---

### **Store the Backup Securely**
The backup file is moved to a dedicated **backup folder** for security.
- Example path: `D:\Backup\samsdb_backup.bat`
- Documentation is stored alongside for reference.

---

## **Logical Recovery(Using Command Line)**

### **Step 1: Navigate to MySQL `bin` Directory**
Open **Command Prompt as Administrator** and run:
```sh
cd C:\Program Files\MySQL\MySQL Server 8.0\bin
```

---

### **Step 2: Execute Database Recovery Command**
Run the following MySQL command to restore the `Technician` table from the backup file:
```sh
mysql.exe -u root -p --database=samsdb --table=Technician < C:\mysql_backup\_1249.sql
```
- **Enter the MySQL password** when prompted.