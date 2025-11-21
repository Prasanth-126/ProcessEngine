# 📘 DB Execute Workflow Setup Guide

## Step 1: Create Administration DB Execute Connection in ACCE
Navigate:  
**Administrative → Workflow Systems → DB Execute Connection → New**

Fill in the following fields:
- **Connection Name**: *(example: FNOS-DB)*
- **Database Type**: *(example: DB2)*
- **Database Name**: *(example: FNOSDB)*
- **Database Host Name**: *(enter host name)*
- **Database Port**: *(example: ******)*
- **DB Username**: *(example: ******)*
- **DB Password**: *(example: ******)*

Then:  
**Next → Validate → OK → Save**

---

## Step 2: Connect to the Server (Remote Connection)
Open **DB2 Command Window** from the search bar.  

Use the following commands:

```bash
db2start                 -- Start the server (optional)
db2 list db directory    -- List all databases in DB2
db2 connect to DB_NAME   -- Connect to a specific database
db2 list tables          -- Show all tables in the database
db2 disconnect DB_NAME   -- Disconnect from the database
```

---

## Step 3: Create a Table
Syntax:

```sql
db2 "CREATE TABLE Table_Name (
    Column1 datatype(size),
    Column2 datatype(size),
    Column3 datatype(size)
)"
```

---

## Step 4: Create a Procedure
Syntax:

```sql
CREATE PROCEDURE Procedure_Name (
    INOUT param1 INT
)
LANGUAGE SQL
BEGIN
    -- Modify the INOUT parameter value
    SET param1 = param1 + 10;
END
```

---

## Step 5: Create Workflow in Process Designer
In the **DBExecute Step**, specify:
1. **Database Connection Alias** → The alias created in ACCE  
2. **Procedure Name** → `SchemaName.Procedure_Name`  
3. **Parameters** → Match the order with table columns  

Then perform:  
**Validate → Check-in → Transfer → Launch Workflow**

Open **PE Administrator → PE Tracker** and complete the task.



⚠️ **Note**: If you encounter any exceptions, refer to *MalFunction* documentation to understand and resolve the error.

---

## Step 6: Verify Data Storage
After successful workflow completion, open **DB2 Command Window** and check data:


By using below command check the data:
```sql
db2 "SELECT * FROM Table_Name"
```
