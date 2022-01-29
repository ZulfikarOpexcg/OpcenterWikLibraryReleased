# Service Util **API**

## REUSABLE FUNCTION
### 1. ProcessResult
This function is used for check the Result of ServiceTransaction MES success or not, this function will return boolean (success/not success) and return string text.
#### **Usage example**
```C#
string sMessage = "";
MoveInService oService = null;
MoveIn oServiceObject = null;
ResultStatus oResulstStatus = null;
oService = new MoveInService(AppSettings.ExCoreUserProfile);
oServiceObject = new MoveIn() { Container = new ContainerRef(ContainerName) };
oResultStatus = oService.ExecuteTransaction(oServiceObject);
bool statusMoveIn = ProcessResult(oResultStatus, ref sMessage, false);
```

### **API**
```C#
bool ProcessResult(ResultStatus Result, ref string ResultMessage, bool IgnoreException = true)
```

### 2. ObjectExists
This function is usedfor check whether certain object is exists or not
#### **Usage example**
```C#
MfgOrderMaintService oService = null;
MfgOrderMaint oServiceObject = null;
//check object exists
oService = new MfgOrderMaintService(AppSettings.ExCoreUserProfile);
bool bObjectExists = ObjectExists(oService, new MfgOrderMaint(), Name);
// Prepare Object
oServiceObject = new MfgOrderMaint();
if (bObjectExists)
{
    oServiceObject.ObjectToChange = new NamedObjectRef(Name);
    oService.BeginTransaction();
    oService.Load(oServiceObject);
}
```

#### **API**
```C#
bool ObjectExists(dynamic ServiceRef, dynamic ServiceObject, string Name)
```

### 3. ObjectExists(revision)

#### **Usage example**
This function is usedfor check whether certain object revision is exists or not
```C#
ProductMaintService oService = null;
ProductMaint oServiceObject = null;
//check object exists
oService = new ProductMaintService(AppSettings.ExCoreUserProfile);
bool bObjectExists = ObjectExists(oService, new ProductMaint(), Name, Revision);
// Prepare Object
oServiceObject = new ProductMaint();
if (bObjectExists)
{
    oServiceObject.ObjectToChange = new RevisionObjectRef(Name);
    oService.BeginTransaction();
    oService.Load(oServiceObject);
}
```

#### **API**
```C#
bool ObjectExists(dynamic ServiceRef, dynamic ServiceObject, string Name, string Revision)
```

### 4. GetDataPointSummaryRef
This function is used for get the objects of the DataCollection, so if we don't know the name of Data Collection, we can used this function to get automatically the DataCollectionDef Object Automatically.

#### **Usage example**
```C#
string DataCollectionName = "";
string DataCollectionRev = "";
MoveInService oService = null;
MoveIn oServiceObject = null;
oService = new MoveInService(AppSettings.ExCoreUserProfile);
DataPointSummary oDataPointSummaryRef = GetDataPointSummaryRef(oService, oServiceObject, new MoveIn_Request(), new MoveIn_Info(), ref DataCollectionName, ref DataCollectionRev);
```

#### **API**
```C#
DataPointSummary GetDataPointSummaryRef(dynamic Service, dynamic ServiceObject, dynamic ServiceObject_Request, dynamic ServiceObject_Info, ref string DataCollectionName, ref string DataCollectionRev)
```

### 5. SetDataPointSummary(DataPointSummaryRef)
This function for set the object data collection, this function commonly is combined with GetDataPointSummaryRef
#### **Usage example**
```C#
string DataCollectionName = "";
string DataCollectionRev = "";
MoveInService oService = null;
MoveIn oServiceObject = null;
oService = new MoveInService(AppSettings.ExCoreUserProfile);
DataPointSummary oDataPointSummaryRef = GetDataPointSummaryRef(oService, oServiceObject, new MoveIn_Request(), new MoveIn_Info(), ref DataCollectionName, ref DataCollectionRev);
oServiceObject.ParametricData = SetDataPointSummary(oDataPointSummaryRef, DataPoints);
```

#### **API**
```C#
DataPointSummary SetDataPointSummary(DataPointSummary DataPointSummaryRef, DataPointDetails[] DataPoints)
```

### 6. SetDataPointSummary( DataPointCollectionRef)
This function for set the object data collection
#### **Usage example**
```C#
string DataCollectionName = "";
string DataCollectionRev = "";
MoveInService oService = null;
MoveIn oServiceObject = null;
oService = new MoveInService(AppSettings.ExCoreUserProfile);
oServiceObject.DataCollectionDef = new RevisionedObjectRef() { Name = DataCollectionName, Revision = DataCollectionRev, RevisionOfRecord = (DataCollectionRev == "") };
oServiceObject.ParametricData = SetDataPointSummary(oServiceObject.DataCollectionDef, DataPoints);
```

#### **API**
```C#
DataPointSummary SetDataPointSummary(object DataCollectionRef, DataPointDetails[] DataPoints)
```

### 7. IsDate
This function for set the object data collection
#### **Usage example**
```C#
ServiceUtil oServiceUtil = new ServiceUtil();
bool result = oServiceUtil.IsDate("05/29/2015 05:50 AM");
```

#### **API**
```C#
bool IsDate(string input)
```

### 8. CanConvertTo
This function for check whether the String can convert to double or not
#### **Usage example**
```C#
ServiceUtil oServiceUtil = new ServiceUtil();
bool result = oServiceUtil.CanCovertTo("3", "System.Double")
```

#### **API**
```C#
bool CanCovertTo(string testString, string testType)
```

## MAINTENANCE FUNCTION
### 1. GetProduct
This function is used for Get the details product from certain String product name
#### **Usage example**
```C#
```
#### **API**
```C#
ProductChanges GetProduct(string ProductName, string ProductRevision = "", bool IgnoreException = true)
```
### 2. GetWorkflow
This function is used for Get the details Workflow from certain String Workflow name
#### **Usage example**
```C#
```
#### **API**
```C#
WorkflowChanges GetWorkflow(string WorkflowName, string WorkflowRevision = "", bool IgnoreException = true)
```
### 3. GetERPRouteFromMfgOrder
This function is used for Get ERP Route from certain string Mfg Order name
#### **Usage example**
```C#
```
#### **API**
```C#
ERPRouteChanges GetERPRouteFromMfgOrder(MfgOrderChanges oMfgOrder, bool IgnoreException = true)
```
### 4. GetERPRoute
This function is used for Get the details ERP Route from certain String ERP Route name
#### **Usage example**
```C#
```
#### **API**
```C#
ERPRouteChanges GetERPRoute(string ERPRouteName, string ERPRouteRevision = "", bool IgnoreException = true)
```
### 5. GetMfgOrder
This function is used for Get the details Mfg Order from certain String Mfg Order name
#### **Usage example**
```C#
```
#### **API**
```C#
MfgOrderChanges GetMfgOrder(string MfgOrderName, bool IgnoreException = true)
```
### 6. GetListMfgOrder
This function is used for Get all the list of Mfg Order
#### **Usage example**
```C#
```
#### **API**
```C#
NamedObjectRef[] GetListMfgOrder(bool IgnoreException = true)
```
### 7. SaveMfgOrder
This function is used for Save a Mfg Order with several parameters
#### **Usage example**
```C#
```
#### **API**
```C#
bool SaveMfgOrder(string Name, string Description = "", string Notes = "", string ProductName = "", string ProductRevision = "", string WorkflowName = "", string WorkflowRevision = "", double Qty = 0, List<dynamic> MaterialList = null, string ERPRoute = "", string PlannedStartDate = "", string PlannedCompletedDate = "", string ReleaseDate = "", string OrderStatus = "", bool AutoCreateQueue = false, bool IgnoreException = true)
```
### 8. SaveProduct
This function for save a Product with several parameters
#### **Usage example**
```C#
```
#### **API**
```C#
bool SaveProduct(string ProductName, string Revision, string IsRevOfRcd = "", string Description = "", string Notes = "", string ProductType = "", string DocumentSet = "", string WorkflowName = "", string WorkflowRevision = "", string BOMName = "", string BOMRevision = "", bool IgnoreException = true)
```
### 9. SaveManageQueue
This function is used for save some material into certain queue, the list material is used List<dynamic>
#### **Usage example**
```C#
```
#### **API**
```C#
bool SaveManageQueue(string oQueue, string oMfgOrder = "", List<dynamic> MaterialQueueDetails = null, bool isActive = true, bool IgnoreException = true)
```
### 10. SaveManageInventory
This function is used for save single material into certain queue
#### **Usage example**
```C#
```
#### **API**
```C#
bool SaveManageInventory(string NameMaterialQueue, string ManageInventory, string ProductNumber, string BatchNumber = "", double Qty = 0, string UOM = "", bool IgnoreException = true)
```

## CONTAINER TXN FUNCTION
### 1. ExecuteRework
This function is used for Executing Rework to the certain Container
#### **Usage example**
```C#
```
#### **API**
```C#
bool ExecuteRework(string ContainerName, string ReworkReason, string Path = "", string Resource = "", bool IgnoreException = true)
```
### 2. ExecuteStart
This function is used for Create or Start a Container
#### **Usage example**
```C#
```
#### **API**
```C#
bool ExecuteStart(string ContainerName, string MfgOrder = "", string ProductName = "", string ProductRevision = "", string WorkflowName = "", string WorkflowRevision = "", string Level = "", string Owner = "", string StartReason = "", string PriorityCode = "", double Qty = 0, string UOM = "", string Comments = "", string EmployeeName = "", string TxnDateStr = "", bool IgnoreException = true)
```
### 3. ExecuteMoveIn
This function is used for Executing MoveIn to the certain Container
#### **Usage example**
```C#
```
#### **API**
```C#
bool ExecuteMoveIn(string ContainerName, string ResourceName, string DataCollectionName = "", string DataCollectionRev = "", DataPointDetails[] DataPoints = null, string CarrierName = "", bool AttachDetachCarrier = false, bool EnforceResource = false, string Comments = "", string EmployeeName = "", string TxnDateStr = "", bool IgnoreException = true)
```
### 4. ExecuteMoveStd
This function is used for Executing MoveStd to the certain Container
#### **Usage example**
```C#
```
#### **API**
```C#
bool ExecuteMoveStd(string ContainerName, string ToResourceName = "", string Resource = "", string DataCollectionName = "", string DataCollectionRev = "", DataPointDetails[] DataPoints = null, string CarrierName = "", bool AttachDetachCarrier = false, string Comments = "", string EmployeeName = "", string TxnDateStr = "", bool IgnoreException = true)
```
### 5. ExecuteComponentIssue
This function is used for Executing Component Issued or comsume Material to the certain Container.
#### **Usage example**
```C#
```
#### **API**
```C#
bool ExecuteComponentIssue(string ContainerName, List<dynamic> IssueDetailList = null, bool IgnoreException = true)
```
### 6. ContainerExists
This function is used for check a container wheter container exists or not
#### **Usage example**
```C#
```
#### **API**
```C#
bool ContainerExists(string ContainerName, bool IgnoreException = true)
```
### 7. GetCurrentContainerStep
This function is used to get the current step from certain container
#### **Usage example**
```C#
```
#### **API**
```C#
string GetCurrentContainerStep(string ContainerName, bool IgnoreException = true)
```
### 8. GetContainerStatusDetails
This function is used for Get the details of container from a certain Container
#### **Usage example**
```C#
```
#### **API**
```C#
CurrentContainerStatus GetContainerStatusDetails(string ContainerName, string DataCollectionName = "", string DataCollectionRev = "", bool IgnoreException = true)
```

## RESOURCE TXN FUNCTION
### 1. GetResourceStatusReasonGroup
This function is used to get the ResourceReasonGroup from Name of Resource Group, or we can get the name from Status Code Reason Group
#### **Usage example**
```C#
```
#### **API**
```C#
ResStatusReasonGroupChanges GetResourceStatusReasonGroup(string StatusCodeName, bool IgnoreException = true)
```
### 2. GetResourceStatusCode
This function is used for get the details of Resource Status Code
#### **Usage example**
```C#
```
#### **API**
```C#
ResourceStatusCodeChanges GetResourceStatusCode(string StatusCodeName, bool IgnoreException = true)
```
### 3. GetListResourceStatusCode
This function is used for get the list of resource status code
#### **Usage example**
```C#
```
#### **API**
```C#
NamedObjectRef[] GetListResourceStatusCode(bool IgnoreException = true)
```
### 4. GetCarrierList
This function is used for get all the list of Carrier Name
#### **Usage example**
```C#
```
#### **API**
```C#
NamedObjectRef[] GetCarrierList(bool IgnoreException = true)
```
### 5. GetResourceStatusDetails
This function is used to get the status of certain resource
#### **Usage example**
```C#
```
#### **API**
```C#
ResourceStatusDetails GetResourceStatusDetails(string ResourceName, bool IgnoreException = true)
```
### 6. GetGetMaintenanceStatus
This function is used to get the list of Maintenance from certain resource name
#### **Usage example**
```C#
```
#### **API**
```C#
GetMaintenanceStatusDetails[] GetGetMaintenanceStatus(string ResourceName, bool IgnoreException = true)
```
### 7. ExecuteResourceSetup
This function is used for set the status of resource
#### **Usage example**
```C#
```
#### **API**
```C#
bool ExecuteResourceSetup(string ResourceName, string Status = "", string Reason = "", string Comments = "", string EmployeeName = "", string TxnDate = "", bool IgnoreException = true)
```
### 8. ExecuteResourceThruput 
This function is used to increase the thruput of certain resource
#### **Usage example**
```C#
```
#### **API**
```C#
bool ExecuteResourceThruput(string ResourceName, double Qty = 0, string UOM = "", string ProductName = "", string ProductRevision = "", string Comments = "", string EmployeeName = "", string TxnDate = "", bool IgnoreException = true)
```

## TEAM TRACKING TXN FUNCTION
### 1. AddTeamMembers
This function is used for add some employee to certain Team
#### **Usage example**
```C#
```
#### **API**
```C#
bool AddTeamMembers(string TeamName, List<dynamic> EmployeeList, bool IgnoreException = true)
```
### 2. RemoveTeamMembers
This function is used for remove some employee to certain Team
#### **Usage example**
```C#
```
#### **API**
```C#
bool RemoveTeamMembers(string TeamName, List<dynamic> EmployeeList, bool IgnoreException = true)
```
