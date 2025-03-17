
## Create Object Types
Define the object types to model the system.

## NOT FINAL in Oracle Object-Relational Database
In Oracle Object-Relational Database, the **`NOT FINAL`** keyword allows **inheritance** in object type definitions. It enables an object type to be **extended (subtyped)** by creating new types based on it.

```sql
CREATE OR REPLACE TYPE model_type AS OBJECT (
    ModelName VARCHAR2(10),
    Manufacture VARCHAR2(20)
) NOT FINAL;

CREATE TYPE submodel_type UNDER model_type (
    SubModelName VARCHAR2(10),
    MaxTakeOffWeight NUMBER(8),
    CruisingRange NUMBER(8),
    WingSpan NUMBER(8),
    Height NUMBER(8,2)
) NOT INSTANTIABLE NOT FINAL;

CREATE TYPE passengersubmodel_type UNDER submodel_type (
    MaxNoOfPassengers NUMBER(8)
);

CREATE TYPE cargosubmodel_type UNDER submodel_type (
    MaxCargoWeight NUMBER(8)
);

CREATE TYPE airline_type AS OBJECT (
    AirlineCode VARCHAR2(8),
    AirlineName VARCHAR2(25)
);

CREATE TYPE aircraft_type AS OBJECT (
    SubModel REF submodel_type,
    Airline REF airline_type,
    AirCraftID NUMBER(8),
    AirCraftName VARCHAR2(25)
);
```
