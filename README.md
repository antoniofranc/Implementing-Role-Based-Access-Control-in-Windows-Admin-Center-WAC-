<img width="441" height="450" alt="image" src="https://github.com/user-attachments/assets/72d66e8b-46f8-46eb-9190-036fefbafe13" />

# Implementing Role-Based Access Control in Windows Admin Center (WAC)

## Lab Scenario
As a network defender, you should be aware of the various tools and tricks available to manage the servers and clients. WAC enables network defenders to perform administrative tasks on any client (except mobile devices). It uses role-based access control (RBAC) to control the activity of the users connected to the server. WAC allows management of system activity such as starting various services, adding and removing resources, and controlling applications.

## Lab Objectives
This lab will demonstrate how to install WAC and configure RBAC in WAC to restrict user activities.

## 🎯 Project Overview of WAC
The Windows Admin Center (WAC) is a web-based administration tool used to manage server and client operating systems, hyper-converged clusters, and failover clusters. Some of the features of WAC are listed below:
- Device management
- Windows event management
- File management
- Firewall management
- Local users and groups management
- Network management
- PowerShell tool
- Process tool
- Registry tool
- Remote desktop
- Role and features
- Services, storage, updates, etc.

In WAC, RBAC provides limited access to users on the target computers. RBAC in WAC works by configuring every managed server with a PowerShell Just-Enough Administration endpoint. The roles are defined by the endpoint. After connecting to the restricted endpoint, a temporary local administrator account is created for managing the machine. If the user is not managing the machine utilizing WAC, then the temporary account will be automatically deleted. When the user connects to the system with the configured RBAC, the WAC will initially check whether or not the user is a local administrator. If the user is a local administrator, then the user can access WAC without restrictions; otherwise, WAC will check whether the user is assigned to any predefined roles. The user will get limited access to the system if the user belongs to a WAC role but is not a full administrator. If the user is not an administrator or a member of a role, then the user will not get access to the machine.

WAC supports the following built-in roles.

`Administrators`: Allows users to use most WAC features without granting them access to Remote Desktop or PowerShell.

`Readers`: Allows users to view information and settings on the server, but not make changes.

`Hyper-V Administrators`: Allows users to make changes to the Hyper-V VMs and switches but limits other features to read-only access.

----

1- Logging into the  computer 

2- Download `https://www.microsoft.com/en-us/evalcenter/download-windows-admin-center`

3- To install WAC, navigate to `Z:\NDE-Tools\NDE Module 02 Identification, Authentication and Authorization\Windows Admin Center` and double-click `WindowsAdminCenter1910.msi`.

4- The installation starts. Check `I accept these terms`. Click `Next` to continue.

<img width="400" height="627" alt="image" src="https://github.com/user-attachments/assets/b91a120e-c33b-4a28-95e8-44737803ac47" />

------

5- The default option pertains to Microsoft updates. Click `Next`.

6- The `Configure Gateway Endpoint` window appears. Click Next to continue.

7- Leave the default settings for port and other options on the window. Click `Install`.

<img width="400" height="578" alt="image" src="https://github.com/user-attachments/assets/c577fd6d-be4b-4e5b-94ed-9b9af36ba000" />

<img width="400" height="578" alt="image" src="https://github.com/user-attachments/assets/262acf48-b5ed-4462-9acd-9cc13e9ab81a" />

---
8- WAC installation starts. If the `User Account Control` window appears, click yes.

9- Installation continues. Check `Open Windows Admin Center`. Click `Finish` to complete the installation.

10- If the list of browser applications pops-up. Select `Microsoft Edge`, Click `OK`.

11- Wait for a few seconds. The Edge browser loads `Windows Admin Center`.

12- If a `Select a certificate for authentication` pop-up appears, click `OK`.

<img width="400" height="655" alt="image" src="https://github.com/user-attachments/assets/267b8040-997c-4a76-aed9-c0ef5fff77a1" />

<img width="400" height="492" alt="image" src="https://github.com/user-attachments/assets/8d0a13ca-5b06-400f-a75c-1e6f97f08106" />

----

13- The `Windows Admin Center` appears. By default, you can see that `Admin Machine-1` is connected and listed under All Connections.

14- Click on the `+Add` button to add the Webserver.

<img width="400" height="768" alt="image" src="https://github.com/user-attachments/assets/8c9dd0c4-c818-459a-a774-d1132c817292" />

<img width="400" height="690" alt="image" src="https://github.com/user-attachments/assets/3d556e31-9f1b-4b03-a0f3-c8d393c03879" />

-----
15- The `Add resources` pane opens. Click `Add` under `Windows Server`.

16- The `Connection tags` pane appears. Type `Webserver` in the `Server name` field. Wait for few seconds.

<img width="400" height="681" alt="image" src="https://github.com/user-attachments/assets/e9f201e7-2828-434f-8cfb-bdee2cfcedb2" />
<img width="400" height="676" alt="image" src="https://github.com/user-attachments/assets/3618f873-8d93-44f6-b00b-aaec6d23c9e1" />

----
17- Select the `Use another account for this connection` radio button, and type the username `Administrator` and password `admin@123`. Click `Add with credentials`.

18- `Webserver` is added to the `Windows Admin Center`.

if `Save password` pop-up appears, click `Never`.

<img width="400" height="635" alt="image" src="https://github.com/user-attachments/assets/33b5994d-da30-4b3a-b72e-029586405cb4" />
<img width="400" height="682" alt="image" src="https://github.com/user-attachments/assets/cee8aa6a-a1c3-454f-9c26-a150c5b1ef6b" />

----
19- Click `Webserver` to connect the server.

20- The `Windows Admin Center` connects to `Webserver` and displays all the tools under the `Server Manager`.

21- We have added `Webserver` to the `Windows Admin Center`. A network defender can now manage the Webserver through WAC.

22- By utilizing the RBAC option in WAC, a network defender can provide only limited access to the user of `Web server` VM. Here, we will see assigning limited access to the already created user (john) in web Server VM. To configure RBAC for user `john`, click `Settings` at the bottom of the `Tools` pane on the left.

23- The `Setting` pane appears. Click `Role-based Access Control`.

<img width="400" height="675" alt="image" src="https://github.com/user-attachments/assets/b5b4e85c-b7f3-49c0-a240-4bde0db14051" />
<img width="400" height="653" alt="image" src="https://github.com/user-attachments/assets/c10a826a-3914-4ca9-bb69-d033e9e69d00" />

-----
24- The `Role-based access control` page appears. Click the `Apply` button at the bottom of the page.

25- The `Restart the WinRM service?` dialog appears. Click `Yes` to continue.

26- A notification (see the `Notifications`  icon at the upper right corner)about scheduling the application of RBAC appears. It takes a maximum of `10 minutes`  to start the RBAC service. Wait for 10 minutes, refresh the `Webserver`  connection.

<img width="400" height="682" alt="image" src="https://github.com/user-attachments/assets/34c1b281-d9af-405a-a4bf-1840a1a3adc9" />
<img width="400" height="240" alt="image" src="https://github.com/user-attachments/assets/323bfb98-d6d3-44c0-bb6d-0b5deb87270d" />

If logged out, `log` in with the credentials for `Webserver` as given in the `Step 17`.

-----
27- Reconnecting to `Webserver` is done. Navigate to `Tools -> Settings`. Click the `Role-based Access Control` option. You can see that the `Role-based access control` status is `Applied`. The `Remove` button appears at the bottom of the page.

If the status of `Role-based access control` does not change to applied, then perform `Steps#23-27` again.

28- RBAC is now added to `Webserver`.

Next, Assign a user to the role. Click `Local users & groups` in the `Tools` pane on the left.

<img width="400" height="582" alt="image" src="https://github.com/user-attachments/assets/32b50d6a-d957-4c88-ae99-d882f8ad0484" />

<img width="400" height="680" alt="image" src="https://github.com/user-attachments/assets/dc50c6de-2ac6-427c-a750-9384cd29d755" />

-----
30- The `Local users & groups` pane appears. Select the user `john` under the `Users` tab.

31- The `Manage membership` option is now visible. If it is not visible, click on More and select `Manage membership` option.

<img width="400" height="685" alt="image" src="https://github.com/user-attachments/assets/217d4721-f527-4510-b01b-8082a18a93c3" />
<img width="400" height="678" alt="image" src="https://github.com/user-attachments/assets/159f622f-cb1b-499e-9fb2-691a1cfb3dd2" />

-----
32- Click `Manage membership` to add the membership to the user. The `Manage membership` pane now opens.

33- Scroll down the list that appears in the `Manage Membership` pane. In the list, uncheck `Users`, and check `Windows Admin Center Readers`. These changes will allow John to view information and settings on the server, but not make changes by assigning the windows admin center readers role. Click `Save`.

34- A notification (See Notifications icon) appears indicating that the membership for the user john has been updated successfully.

<img width="400" height="672" alt="image" src="https://github.com/user-attachments/assets/b925fb87-db44-40d8-b758-0e1ff3a11e7c" />
<img width="400" height="640" alt="image" src="https://github.com/user-attachments/assets/4c8b235a-f41c-4978-97dd-64a0c4726ac6" />

----
35- Click `Windows Admin Center` from top-left corner of the dashboard, to navigate to the Home page.

36- Select `Webserver` and click the `Manage as` tab. If `Manage as` tab is not visible, click on `More` tab and select `Manage as` option.

<img width="400" height="679" alt="image" src="https://github.com/user-attachments/assets/24fa2f6a-165b-482f-aa91-def7c9379d94" />

<img width="400" height="679" alt="image" src="https://github.com/user-attachments/assets/c07f5d7f-b01a-495e-93b8-aef0a8fc2613" />

-----
37- Specify your credentials once the pane opens. Change username to `John` and password to `user@123`. We will now log in as a user to `Webserver`. In `Windows Admin Center`, click `Continue`.

38- Wait for a few seconds; `Webserver in` WAC is loaded for user `john`. You can see that the user `john` is selected under `Managing as`. Click `Webserver` link to connect.

<img width="400" height="674" alt="image" src="https://github.com/user-attachments/assets/2a48d275-c93b-471f-871a-958ff54dde0d" />
<img width="400" height="322" alt="image" src="https://github.com/user-attachments/assets/4b63abf4-a9f0-4e7f-8cb8-3cd59b355307" />

-----
39- Since we have logged in as `John` to `Windows Admin Center`, `Webserver` is connected with limited access (It is shown at the upper left corner as `Webserver (Limited Access)`.

40- As a user of `Webserver`, you can try to add new storage to it. But, as we have added the user john in RBAC and allowed for limited access permission only, the system will not allow user `John` to add new storage.

41- Click `Storage` in the Tools pane. Wait for a few seconds; the `Storage` pane appears on the right side of the window.

<img width="400" height="684" alt="image" src="https://github.com/user-attachments/assets/6905c404-7050-44c6-9156-6a0ece307415" />

<img width="400" height="634" alt="image" src="https://github.com/user-attachments/assets/6324c423-2c33-41d7-8318-191bdf9f25c0" />

----
42- Under the `Disks` menu on the `Storage` pane, click `More` and select `Create VHD` option.

43- The Create VHD pane opens. Type the following in the respective fields. Click Submit.

VHD folder path: `c:\TestFolder`

New VHD file name: `test`

File extension: `vhd`

Size (GB): `1`

Virtual hard disk type: `Fixed`

<img width="400" height="682" alt="image" src="https://github.com/user-attachments/assets/d133907c-d652-4dc8-a8c6-954cb4d756d4" />

<img width="400" height="683" alt="image" src="https://github.com/user-attachments/assets/e1435258-4d48-4a13-8625-8c3218813afb" />

------
44- The following error notification appears (See `Notifications` icon): `Couldn't create the VHD`. `Error Exception: This operation was blocked by role-based access control settings`.

<img width="400" height="639" alt="image" src="https://github.com/user-attachments/assets/052a4245-e4cf-4cd4-aae6-f8a0da4480ab" />

45- As described above, a network defender can utilize the Windows Admin Center tool for managing the system resources and permissions.

46- Close all the opened windows.

-----

- Technologies: Windows Server, Windows Admin Center, PowerShell JEA, RBAC, WinRM, Active Directory
- Domain: Cybersecurity, Network Defense, Identity & Access Management
- Completion Date: October 2025









