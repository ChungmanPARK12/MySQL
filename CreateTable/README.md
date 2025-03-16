
## Create Tables for Object Types
Tables are created based on the defined object types.

## Difference Between Object Types in Oracle and MySQL

**Oracle's Object-Relational model** is quite different from **MySQL’s relational model**. While **Oracle supports object types**, **MySQL primarily focuses on relational databases** and does not natively support **object-oriented features like `CREATE TYPE AS OBJECT`**.

```sql
CREATE TABLE model_table OF model_type;

CREATE TABLE passengersubmodel_table OF passengersubmodel_type;

CREATE TABLE cargosubmodel_table OF cargosubmodel_type;

CREATE TABLE airline_table OF airline_type (
    AirlineCode NOT NULL
);

CREATE TABLE aircraft_table OF aircraft_type (
    AirCraftID NOT NULL
);

```
