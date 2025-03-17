
## Assign Primary & Foreign Keys
Tables are created based on the defined object types.

```sql
ALTER TABLE aircraft_table
ADD CONSTRAINT aircraftID_pk PRIMARY KEY (AirCraftID);

ALTER TABLE airline_table
ADD CONSTRAINT airlinecode_pk PRIMARY KEY (AirlineCode);

ALTER TABLE model_table
ADD CONSTRAINT model_pk PRIMARY KEY (ModelName, Manufacture);

ALTER TABLE cargosubmodel_table
ADD CONSTRAINT cargosubmodel_pk PRIMARY KEY (ModelName, Manufacture, SubModelName);

ALTER TABLE passengersubmodel_table
ADD CONSTRAINT passengersubmodel_pk PRIMARY KEY (ModelName, Manufacture, SubModelName);

ALTER TABLE cargosubmodel_table
ADD CONSTRAINT cargo_model_fk FOREIGN KEY (ModelName, Manufacture)
REFERENCES model_table(ModelName, Manufacture);

ALTER TABLE passengersubmodel_table
ADD CONSTRAINT passenger_model_fk FOREIGN KEY (ModelName, Manufacture)
REFERENCES model_table(ModelName, Manufacture);

```
