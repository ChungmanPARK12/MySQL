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

### **Granting Roles to Users and Setting Default Roles**
To assign the **human_resources** role to a user and set it as their default role, use the following SQL statements:

```sql
-- Grant the human_resources role to user Jake
GRANT 'human_resources' TO 'Jake'@'%';

-- Set the default role for Jake
SET DEFAULT ROLE 'human_resources' TO 'Jake'@'%';

-- Verify granted privileges
SHOW GRANTS FOR 'Jake'@'%';
```
![Image](https://github.com/user-attachments/assets/6136e89f-9acc-48b1-98a4-2183db8dc1e6)
