## Understanding Data Insertion in Oracle

This SQL script inserts data into **object-relational tables** in Oracle. It separates **objects, primary keys, and foreign keys** while maintaining **data integrity**.

### **Object Types**
- **Airline, Model, CargoSubmodel, and PassengerSubmodel** are **object types**.
- These define the structure for storing airline and aircraft-related data.

### **Primary Key Usage**
- Each table has a **Primary Key (PK)** to ensure **uniqueness**.
- Example: `AirlineCode` in `airline_table` uniquely identifies each airline.
- `ModelName` and `Manufacture` together form a **composite primary key** in `model_table`.

```sql
ALTER TABLE model_table ADD CONSTRAINT model_pk PRIMARY KEY (ModelName, Manufacture);
```

## Insert Data into Tables
Populate tables with sample data.

```sql
-- Inserting Airlines(AirlineCode, AirlineName)
INSERT INTO airline_table VALUES ('AR01', 'Airline 1');
INSERT INTO airline_table VALUES ('AR02', 'Airline 2');
INSERT INTO airline_table VALUES ('AR03', 'Airline 3');

-- Inserting Models
INSERT INTO model_table VALUES ('737', 'Boeing');
INSERT INTO model_table VALUES ('747', 'Boeing');

-- Inserting Cargo Submodels
INSERT INTO cargosubmodel_table VALUES ('737', 'Boeing', 'LightCargo', 5000, 500, 75, 40, 4200);
INSERT INTO cargosubmodel_table VALUES ('767', 'Boeing', 'MedCargo', 8000, 500, 75, 40, 7200);
INSERT INTO cargosubmodel_table VALUES ('747', 'Boeing', 'HeavyCargo', 11000, 500, 75, 40, 10200);

-- Inserting Passenger Submodels
INSERT INTO passengersubmodel_table VALUES ('737', 'Boeing', 'LightPass', 5000, 500, 75, 40, 200);
INSERT INTO passengersubmodel_table VALUES ('767', 'Boeing', 'MedPass', 8000, 500, 75, 40, 350);
INSERT INTO passengersubmodel_table VALUES ('747', 'Boeing', 'HeavyPass', 11000, 500, 75, 40, 700);

```
