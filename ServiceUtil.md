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