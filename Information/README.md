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
- **Airline** (**AirlineId**, AirlineName, AddressStreet, AddressSuburb, AddressPostCode, AddressState, AddressCountry, ContactPhone, WebsiteAddress, 🟥**Country_CountryId**)
- **Country** (**CountryId**, CountryName)
- **Aircraft** (**AircraftId**, AircraftName, <span style="color:red">Airline_AirlineId</span>, <span style="color:red">AircraftModel_ModelId</span>, <span style="color:red">AircraftModel_Manufacturer_ManufacturerId</span>, <span style="color:red">Engine_EngineIdentifycationNo</span>)
- **AircraftModel** (ModelId, ModelName, Manufacturer_ManufacturerId)
- **Technician** (EmployeeId, FirstName, LastName, LoginName, Salary, AddressState, AddressSuburb, AddressPostCode, Phone, Aircraft_AircraftId, Technician_EmployeeId, Training_TrainingId)
- **SubModel** (SubModelId, SubModelName, SubModelDescription, Length, Height, WingSpanArea, MaxPayloadWeight, MaxCruisingSpeed, MaxRange, Aircraft_AircraftId, EngineModel_EngineModelId)
- **Manager** (ManagerId, FirstName, LastName, LoginName, Salary, Technician_EmployeeId)
- **Training** (TrainingId, TrainingName, TrainingDate)
- **EngineModel** (EngineModelId, EngineModelName, MadeBy, ThrustRange, DryWeight)
- **Engine** (EngineIdentificationNo, Manufacturer_ManufacturerId)
- **Manufacturer** (ManufacturerId, ManufacturerName)
- **TestEvent** (EventId, DateTimeStart, DateTimeEnd, HoursTechnician, ResultTest, TestResultENUM, ResultComment, AircraftModel_ModelId, AircraftModel_Manufacturer_ManufacturerId, Test_TestId)
- **Test** (TestId, TestName, TestItems, TestItem_TestItemCode)
- **TestItem** (TestItemCode, NameTestItem)
- **TestItemTestEvent** (TestEvent_EventId, TestItem_TestItemCode)
- **TechnicianTestItemTestEvent** (Technician_EmployeeId, TestItemTestEvent_TestEvent_EventId, TestItemTestEvent_TestItem_TestItemCode)