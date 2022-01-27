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

# License & Copy Right
© M. Zulfikar Isnaen [MIT License](LICENSE).