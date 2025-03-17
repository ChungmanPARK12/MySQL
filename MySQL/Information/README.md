# **Requirements**

## Database Schema

### **Tables and Attributes**
- **Airline** (**AirlineId**, AirlineName, AddressStreet, AddressSuburb, AddressPostCode, AddressState, AddressCountry, ContactPhone, WebsiteAddress, **Foreign Key:** Country_CountryId)
- **Country** (**CountryId**, CountryName)
- **Aircraft** (**AircraftId**, AircraftName, **Foreign Key:** Airline_AirlineId, AircraftModel_ModelId, AircraftModel_Manufacturer_ManufacturerId, Engine_EngineIdentifycationNo)
- **AircraftModel** (**ModelId**, ModelName, **Foreign Key:** Manufacturer_ManufacturerId)
- **Technician** (**EmployeeId**, FirstName, LastName, LoginName, Salary, AddressState, AddressSuburb, AddressPostCode, Phone, **Foreign Key:** Aircraft_AircraftId, Technician_EmployeeId, Training_TrainingId)
- **SubModel** (**SubModelId**, SubModelName, SubModelDescription, Length, Height, WingSpanArea, MaxPayloadWeight, MaxCruisingSpeed, MaxRange, **Foreign Key:** Aircraft_AircraftId, EngineModel_EngineModelId)
- **Manager** (**ManagerId**, FirstName, LastName, LoginName, Salary, **Foreign Key:** Technician_EmployeeId)
- **Training** (**TrainingId**, TrainingName, TrainingDate)
- **EngineModel** (**EngineModelId**, EngineModelName, MadeBy, ThrustRange, DryWeight)
- **Engine** (EngineIdentificationNo, **Foreign Key:** Manufacturer_ManufacturerId)
- **Manufacturer** (**ManufacturerId**, ManufacturerName)
- **TestEvent** (**EventId**, DateTimeStart, DateTimeEnd, HoursTechnician, ResultTest, TestResultENUM, ResultComment, **Foreign Key:** AircraftModel_ModelId, AircraftModel_Manufacturer_ManufacturerId, Test_TestId)
- **Test** (**TestId**, TestName, TestItems, **Foreign Key:** TestItem_TestItemCode)
- **TestItem** (**TestItemCode**, NameTestItem)
- **TestItemTestEvent** (**Foreign Key:** TestEvent_EventId, TestItem_TestItemCode)
- **TechnicianTestItemTestEvent** (**Foreign Key:** Technician_EmployeeId, TestItemTestEvent_TestEvent_EventId, TestItemTestEvent_TestItem_TestItemCode)

## Entity Relationships and Business Rules

- **Each Aircraft owns 0, 1, or many AircraftModels.**
  - Each AircraftModel must be owned by one and only one Aircraft.

- **Each Aircraft owns 0, 1, or many SubModels.**
  - Each SubModel must be owned by one and only one Aircraft.

- **Each Aircraft owns 0, 1, or many Technicians.**
  - Each Technician must be owned by one and only one Aircraft.

- **Each Aircraft owns 0, 1, or many Engines.**
  - Each Engine must be owned by one and only one Aircraft.

- **Each Manufacturer owns 0, 1, or many Engines.**
  - Each Engine must be owned by one and only one Manufacturer.

- **Each Technician owns 0, 1, or many Managers.**
  - Each Manager must be owned by one and only one Technician.

- **Each Technician owns 0, 1, or many Trainings.**
  - Each Training must be owned by one and only one Technician.

- **Each Engine owns 0, 1, or many SubModels.**
  - Each SubModel must be owned by one and only one EngineModel.

