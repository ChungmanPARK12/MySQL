## **Indexing Strategy for Performance Optimization**
One key aspect of **physical database design** is **creating indexes** to improve **query performance**. 

### **Indexing Guidelines**
- Indexes should be applied to **frequently used foreign key attributes**.
- They should be used in columns appearing in **WHERE clauses** and **ORDER BY statements**.
- **Primary keys** are automatically indexed, but **foreign keys are not**, requiring manual indexing.

### **Required Indexes**
Indexes must be created for the **foreign keys** in the following tables:
- `AircraftModel`
- `AircraftSubModel`
- `Aircraft`

### **CREATE INDEX Statements**
```sql
-- Index for AircraftModel foreign key
CREATE INDEX idx_aircraft_model_manufactureid ON AircraftModel(ManufacturerID);

-- Indexes for AircraftSubModel foreign keys
CREATE INDEX idx_aircraft_sub_model_aircraft_id ON AircraftSubModel(AircraftID);
CREATE INDEX idx_aircraft_sub_model_engine_model_id ON AircraftSubModel(EngineModelID);

-- Indexes for Aircraft foreign keys
CREATE INDEX idx_aircraft_airline_id ON Aircraft(AirlineID);
CREATE INDEX idx_aircraft_aircraft_model_model_id ON Aircraft(AircraftModelModelID);
```
## **User Permissions and Role-Based Access Control**
To ensure **secure access control**, user roles must be created and granted specific privileges. The database should allow **Human Resources** and **Technicians** to access relevant tables without exposing sensitive information.

### **User Permission Guidelines**
- The **Human Resources role** should have full access to manage technician and training records.
- The **Technician role** should have restricted access based on operational needs.

### **Required SQL Statements for Granting User Permissions**
```sql
-- Create human resources role
CREATE ROLE 'human_resources';

-- Grant privileges to human_resources role
GRANT ALL PRIVILEGES ON samsdb.Technician TO 'human_resources';
GRANT ALL PRIVILEGES ON samsdb.Training TO 'human_resources';
GRANT ALL PRIVILEGES ON samsdb.TechnicianTrainingAircraftModel TO 'human_resources';

-- Verify granted privileges
SHOW GRANTS FOR 'human_resources'@'%';
```
![Image](https://github.com/user-attachments/assets/e4473aa2-57eb-403b-a65a-87341243f557)
---


### **Granting Roles to Users and Setting Default Roles**
To assign the **human_resources** role to a user and set it as their default role, use the following SQL statements:

```sql
-- Grant the human_resources role to user Jake
GRANT 'human_resources' TO 'Jake'@'%';

-- Set the default role for lake
SET DEFAULT ROLE 'human_resources' TO 'Jake'@'%';

-- Verify granted privileges
SHOW GRANTS FOR 'Jake'@'%';
```
![Image](https://github.com/user-attachments/assets/6136e89f-9acc-48b1-98a4-2183db8dc1e6)

### **Inserting Encrypted Data**
```sql
INSERT INTO EncryptedTechnicianAircraftModelTraining (id, technicianId, aircraftModelId, trainingStartDate, trainingEndDate)
VALUES (
  1,
  123,
  456,
  AES_ENCRYPT('2023-01-01', 'encryption_key'),
  AES_ENCRYPT('2023-02-01', 'encryption_key')
);
```
![Image](https://github.com/user-attachments/assets/9a527399-e2db-4357-bb2e-a69e5464bb49)
```sql
INSERT INTO EncryptedTestEvent (id, eventId, technicianId, eventDate, result)
VALUES (
  1,
  789,
  123,
  AES_ENCRYPT('2023-03-15', 'encryption_key'),
  AES_ENCRYPT('Passed', 'encryption_key')
);
```
![Image](https://github.com/user-attachments/assets/93d28e20-0e73-4cb5-aed0-3482d3ca4c1e)

### **Decrypting Data for Reading**
To retrieve and decrypt the encrypted data:
```sql
SELECT 
  id,
  technicianId,
  aircraftModelId,
  CAST(AES_DECRYPT(trainingStartDate, 'encryption_key') AS CHAR) AS trainingStartDate,
  CAST(AES_DECRYPT(trainingEndDate, 'encryption_key') AS CHAR) AS trainingEndDate
FROM EncryptedTechnicianAircraftModelTraining;
```
```sql
SELECT 
  id,
  eventId,
  technicianId,
  eventDate,
  CAST(AES_DECRYPT(result, 'encryption_key') AS CHAR) AS result
FROM EncryptedTestEvent;
```

## **Data Insertion SQL Statements**

### **Airline**
```sql
INSERT INTO samsdb.airline (AirlineId, AirlineName, AddressStreet, AddressSuburb, AddressPostCode, AddressState, AddressCountry, ContactPhone, WebsiteAddress, Country_CountryId) 
VALUES ('QF', 'Qantas', 'Colin', 'Findon', '5120', 'SA', 'Australia', '0411345678', 'www.qantas.com', NULL);

INSERT INTO samsdb.airline (AirlineId, AirlineName, AddressStreet, AddressSuburb, AddressPostCode, AddressState, AddressCountry, ContactPhone, WebsiteAddress, Country_CountryId) 
VALUES ('DS', 'Dagan', 'Henley', 'WestBeach', '5121', 'SA', 'Australia', '0422345678', 'www.dahan.com', NULL);
```

### **Country**
```sql
INSERT INTO samsdb.country (CountryID, CountryName) VALUES (1, 'Australia');
INSERT INTO samsdb.country (CountryID, CountryName) VALUES (2, 'Singapore');
```

### **Aircraft**
```sql
INSERT INTO samsdb.aircraft (AircraftId, AircraftName, Airline_AirlineId, AircraftModel_ModelId, AircraftModel_Manufacturer_ManufacturerId, Engine_EngineIdentificationNo) 
VALUES (737, 'A737', NULL, NULL, NULL, NULL);

INSERT INTO samsdb.aircraft (AircraftId, AircraftName, Airline_AirlineId, AircraftModel_ModelId, AircraftModel_Manufacturer_ManufacturerId, Engine_EngineIdentificationNo) 
VALUES (738, 'A738', NULL, NULL, NULL, NULL);
```

### **AircraftModel**
```sql
INSERT INTO samsdb.aircraftmodel (ModelId, ModelName, Manufacturer_ManufacturerId) VALUES ('M1', 'MA737', NULL);
INSERT INTO samsdb.aircraftmodel (ModelId, ModelName, Manufacturer_ManufacturerId) VALUES ('M2', 'MA738', NULL);
```

### **Submodel**
```sql
INSERT INTO samsdb.submodel (SubModelId, SubModelName, SubModelDescription, Length, Height, WingSpanArea, MaxPayloadWeight, MaxCruisingSpeed, MaxRange, Aircraft_AircraftId, EngineModel_EngineModelId) 
VALUES ('SM737A', 'ABA-Flight', 'Flight to Australia', 45.5, 12.5, 35.9, 1000.00, 850, 6110, NULL, NULL);

INSERT INTO samsdb.submodel (SubModelId, SubModelName, SubModelDescription, Length, Height, WingSpanArea, MaxPayloadWeight, MaxCruisingSpeed, MaxRange, Aircraft_AircraftId, EngineModel_EngineModelId) 
VALUES ('SM738A', 'SSA-Flight', 'Flight to Singapore', 50.5, 15.5, 29.9, 1010.00, 750, 6000, NULL, NULL);
```

### **Technician**
```sql
INSERT INTO samsdb.technician (EmployeeId, FirstName, LastName, LoginName, Salary, AddressState, AddressSuburb, AddressPostCode, Phone, Aircraft_AircraftId, Technician_EmployeeId, Training_TrainingId) 
VALUES (1, 'Boseong', 'Kim', 'Kim', 1200.00, 'SA', 'Adelaide', '5120', '0011345345', NULL, NULL, NULL);

INSERT INTO samsdb.technician (EmployeeId, FirstName, LastName, LoginName, Salary, AddressState, AddressSuburb, AddressPostCode, Phone, Aircraft_AircraftId, Technician_EmployeeId, Training_TrainingId) 
VALUES (2, 'Melissa', 'Smith', 'Smith', 1100.00, 'SA', 'Adelaide', '5120', '0111345345', NULL, NULL, NULL);
```

### **Manager**
```sql
INSERT INTO samsdb.manager (ManagerId, FirstName, LastName, LoginName, Salary, Technician_EmployeeId) 
VALUES (1, 'Monson', 'Kim', 'Kim', 1200, NULL);

INSERT INTO samsdb.manager (ManagerId, FirstName, LastName, LoginName, Salary, Technician_EmployeeId) 
VALUES (2, 'Heachan', 'Lee', 'Lee', 1200, NULL);
```

### **Training**
```sql
INSERT INTO samsdb.training (TrainingID, TrainingName, TrainingDate) 
VALUES (1, 'EngineTraining', '2022-01-01');

INSERT INTO samsdb.training (TrainingID, TrainingName, TrainingDate) 
VALUES (2, 'WingTraining', '2022-01-02');
```

### **Engine**
```sql
INSERT INTO samsdb.engine (EngineIdentificationNo, Manufacturer_ManufacturerId) 
VALUES (11, NULL);

INSERT INTO samsdb.engine (EngineIdentificationNo, Manufacturer_ManufacturerId) 
VALUES (12, NULL);
```

### **EngineModel**
```sql
INSERT INTO samsdb.enginemodel (EngineModelId, EngineModelName, MadeBy, ThrustRange, DryWeight) 
VALUES (1, 'CMD-12', 'Korea', 12.5, 50.00);

INSERT INTO samsdb.enginemodel (EngineModelId, EngineModelName, MadeBy, ThrustRange, DryWeight) 
VALUES (2, 'CMD-11', 'Australia', 13.5, 60.00);
```

### **Manufacturer**
```sql
INSERT INTO samsdb.manufacturer (ManufacturerId, ManufacturerName) 
VALUES (1, 'PCI');

INSERT INTO samsdb.manufacturer (ManufacturerId, ManufacturerName) 
VALUES (2, 'Pfizer');
```
