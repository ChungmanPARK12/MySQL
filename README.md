# **Southern Airport Maintenance Service Database Project**

<p align="center">
  <img 
    src="https://github.com/user-attachments/assets/598fa6ce-f6e5-41dc-87b6-0d19b829cbe4"
    width="700"
    height="auto"
  />
</p>


## **Project Overview**

This project was completed as part of a database design and implementation assignment.  
The objective was to design a **MySQL relational database** for a fictional organisation, *Southern Airport Maintenance Service*, to manage information related to **aircraft**, **technicians**, and **maintenance activities**.

The project focuses on understanding and applying the **core stages of database development**, including:

- Analysing system requirements  
- Designing a logical data model (ERD)  
- Translating the logical model into a physical database schema  
- Implementing tables and relationships using MySQL  
- Preparing a basic backup strategy  

### 1. Information Background

This section summarises the **database requirements**, including key entities, attributes, and business rules, which provide the basis for the logical and physical design stages.

 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/MySQL/Information)

### 2. Logical Design

This section presents the **Entity Relationship Diagram (ERD)**, illustrating the logical structure of the database and the relationships between entities based on the defined business rules.

 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/MySQL/LogicalDesign)

### 3. Physical Design

This section covers the **physical implementation** of the database, including indexing, user access control, data encryption, and data insertion using MySQL.

 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/MySQL/PhysicalDesign)

### 4. Backup

This section demonstrates **logical backup and recovery** of the MySQL database using both **MySQL Workbench** and **command-line tools**.

 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/MySQL/Backup)

---

## **Oracle Object-Relational Database: Aircraft System**
<p align="center">
  <img 
    src="https://github.com/user-attachments/assets/4d8b5591-226a-45a5-b87e-ddf7c0456086"
    width="700"
    height="auto"
  />
</p>

### **Aircraft Submodel and Airline Relationship**
- **A Submodel** is a type of **Model**. (_Abstract Class_)
- **Passenger Submodel** and **Cargo Submodel** inherit from **Submodel**.
- Each **Aircraft** belongs to either a **Passenger** or **Cargo Submodel**.
- Each **Airline** may have **0, 1, or many Aircraft**.
- Each **Aircraft** must belong to **one and only one Airline**.

![Image](https://github.com/user-attachments/assets/6c9b7ab2-7d17-4f6d-b869-a412fcdda905)

### 1. Create Object Types

This section defines **Oracle object types** to model the system using object-relational features such as inheritance, subtypes, and references.

 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/Oracle/CreateObject)

### 2. Create Tables

This section creates **object tables** in Oracle based on the defined object types and contrasts Oracle’s object-relational model with MySQL’s relational approach.

 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/Oracle/CreateTable)

### 3. Assign Primary & Foreign Keys

This section defines **primary and foreign key constraints** to enforce entity integrity and relationships between Oracle object tables.

 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/Oracle/AssignKey)

### 4. Data Insertion

This section demonstrates **data insertion** into Oracle object-relational tables while preserving primary and foreign key integrity.


 - [View result](https://github.com/ChungmanPARK12/MySQL/tree/766ec6c6c98b89e48fe452c28619d0918198e6b7/Oracle/InsertData)
 
## **Project Summary**

This project presents a complete database solution for *Southern Airport Maintenance Service* using both **MySQL** and **Oracle**.

- **MySQL**: Covers logical/physical design, backups, and data insertion.
- **Oracle**: Demonstrates object-relational design with custom object types and relationships.

It highlights my skills in building structured, scalable databases using both relational and object-oriented approaches.
