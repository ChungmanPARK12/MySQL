# **Requirements**

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

## Database Schema

### **Tables and Attributes**
- **Airline** (**AirlineId**, AirlineName, AddressStreet, AddressSuburb, AddressPostCode, AddressState, AddressCountry, ContactPhone, WebsiteAddress, **Primary Key:** Country_CountryId)
- **Country** (**CountryId**, CountryName)
- **Aircraft** (**AircraftId**, AircraftName, **Primary Key:** Airline_AirlineId, AircraftModel_ModelId,AircraftModel_Manufacturer_ManufacturerId, Engine_EngineIdentifycationNo)
- **AircraftModel** (**ModelId**, ModelName, **Primary Key:** Manufacturer_ManufacturerId)
- **Technician** (**EmployeeId**, FirstName, LastName, LoginName, Salary, AddressState, AddressSuburb, AddressPostCode, Phone, **Primary Key:** Aircraft_AircraftId, Technician_EmployeeId, Training_TrainingId)
- **SubModel** (**SubModelId**, SubModelName, SubModelDescription, Length, Height, WingSpanArea, MaxPayloadWeight, MaxCruisingSpeed, MaxRange, **Primary Key:** Aircraft_AircraftId, EngineModel_EngineModelId)
- **Manager** (**ManagerId**, FirstName, LastName, LoginName, Salary, **Primary Key:** Technician_EmployeeId)
- **Training** (**TrainingId**, TrainingName, TrainingDate)
- **EngineModel** (**EngineModelId**, EngineModelName, MadeBy, ThrustRange, DryWeight)
- **Engine** (EngineIdentificationNo, **Primary Key:** Manufacturer_ManufacturerId)
- **Manufacturer** (**ManufacturerId**, ManufacturerName)
- **TestEvent** (**EventId**, DateTimeStart, DateTimeEnd, HoursTechnician, ResultTest, TestResultENUM, ResultComment, **Primary Key:** AircraftModel_ModelId, AircraftModel_Manufacturer_ManufacturerId, Test_TestId)
- **Test** (**TestId**, TestName, TestItems, **Primary Key:** TestItem_TestItemCode)
- **TestItem** (**TestItemCode**, NameTestItem)
- **TestItemTestEvent** (**Primary Key:** TestEvent_EventId, TestItem_TestItemCode)
- **TechnicianTestItemTestEvent** (**Primary Key:** Technician_EmployeeId, TestItemTestEvent_TestEvent_EventId, TestItemTestEvent_TestItem_TestItemCode)

