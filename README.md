# How to use the library `.dll`
## Add reference `.dll` in your project:
- Camstar.Exceptions.dll
- Camstar.Util.dll
- Camstar.WCFClient.dll
- Camstar.WCFClientBase.dll
- InSiteXMLClient.dll
- OpcenterWikLibrary.dll </br></br>

![Add Reference](./Images/AddReference1.jpg)

## Replace `App.config`
Rename `App.config.example` to `App.config` and changes your configuration inside there. Notes: **Password is used Encrypted String**

## Copy `Endpoints.config`
Copy `Endpoints.config` into your project. and make properties Copy to Output = Copy always. </br></br>
![End Points](./Images/Endpoints.jpg)

Edit all URL inside `Endpoints.config` based on the `Opcenter Server`, for example:
```
https://excr86mio40/CamstarWCFServices/QueryService.svc

to

https://<your mes server>/CamstarWCFServices/QueryService.svc
```

# Add Assembly Name in `Program.cs`
This is very **important** steps!
Add syntax below in your `Program.cs` inside `static void Main(string[] args){}`
```C#
AppSettings.AssemblyName = System.Reflection.Assembly.GetExecutingAssembly().GetName().Name;
```
For Example
```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace LaserPrinting
{
    static class Program
    {
        [STAThread]
        static void Main()
        {
            AppSettings.AssemblyName = System.Reflection.Assembly.GetExecutingAssembly().GetName().Name; // This one, add in your project !!!
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new Main());
        }
    }
}

```

# Enabled Event Log on windows Machine
- Log on to the computer as an administrator.
- Click Start, click Run, type Regedit in the Open box, and then click OK. - The Registry Editor window appears.
- Locate the following registry subkey
```
Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog
```
- Right-click Eventlog, and then click Permissions. The Permissions for Eventlog dialog box appears.

![Permission Event Log](./Images/EventLogPermission1.jpg)

- Click Add, add the user account or group that you want and set the following permissions: `Full Control`.

![Permission Event Log](./Images/EventLogPermission2.jpg)

- Locate the following registry subkey
```
Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog\Security
```

![Permission Event Log](./Images/EventLogPermission3.jpg)

- Click Add, add the user account or group that you want and set the following permissions: `Full Control`.

![Permission Event Log](./Images/EventLogPermission4.jpg)

# Documentation API
- [Service Util API](./ServiceUtil.md)

# Released Notes
- [Released v1.0.0](https://github.com/ZulfikarOpexcg/OpcenterWikLibraryReleased/releases/tag/v1.0.0) 
- [Released v1.0.1](https://github.com/ZulfikarOpexcg/OpcenterWikLibraryReleased/releases/tag/v1.0.1)  
    - Fixing Security issued ExCoreProfile
    - Add `UNCFolderPath` Class, there's two method, `Connect()` and `Disconnect()`
- [Released v1.0.2](https://github.com/ZulfikarOpexcg/OpcenterWikLibraryReleased/releases/tag/v1.0.2)  
    - Update the Mfg Order
    - Add isImageChanges, DocumentChanges, DocumentSetChanges, MfgOrderChanges, ResourceChanges  
- [Released v1.0.3](https://github.com/ZulfikarOpexcg/OpcenterWikLibraryReleased/releases/tag/v1.0.3)  
    - **ExecuteContainerAttrMaint** = This function is used to store data and attach container, this value will move alongside with the container.
- [Released v1.0.4](https://github.com/ZulfikarOpexcg/OpcenterWikLibraryReleased/releases/tag/v1.0.4)
    - **GetFinishGoodRecord** = This function is used for Getting all the record Container within the Mfg Order. And this function must be used Asynchronous method, otherwise will freeze your application.
    - **GetCounterFromMfgOrder** = This function is used for counting the unit for specific resource (Unit Counter), and the return is integer.
# License & Copy Right
© M. Zulfikar Isnaen [MIT License](LICENSE).