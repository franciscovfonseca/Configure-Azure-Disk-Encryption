<br>

<p align="center">
<img width="500" src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/5795419a-3012-4a57-b4b0-155c2dd93fc7" alt="Microsoft Active Directory Logo"/>
<br>
<br>
<br>



<h1> Configure Azure Disk Encryption</h1>
<br>

<h2>Understanding the Scenario</h2>

<br>

You are a Security Engineer for an organization that needs you to enable **Azure Disk Encryption** on a **Azure Virtual Machine**.


1. First, you will **Create a Virtual Machine**.

2. Next, you will **Add a Data Disk to the Virtual Machine**.

4. Finally, you will **Enable Azure Disk Encryption**.

<br>

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/01f390c9-cd83-447f-bb40-6c76a64dfa06" height="70%" width="70%" alt="9"/><br />

<br>
<br>

<br>

<h2>1️⃣ Create an Azure Virtual Machine</h2>
<br>

On the Azure portal home page, select **Virtual machines**, and then select **+ Create**.
<br>

Select **Azure virtual machine**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/c09db8dc-a7ac-4ba5-9008-47c752f0a9bb" height="100%" width="100%" alt="9"/><br />
<br>

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/8dec1459-c811-4957-a229-11219200669e" height="50%" width="50%" alt="9"/><br />
<br>

On the Create a virtual machine blade, on the Basics page, in Resource group, select **corp-datalod42311660**.
<br>

In Virtual machine name, enter ***🆃 webVM1***, and then in Image, select **Windows Server 2019 Datacenter - x64 Gen2**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/22ec1eb9-1bf0-4d11-a145-1b987aecfaca" height="80%" width="80%" alt="9"/><br />
<br>

In Size, select **See all sizes**.
<br>

On the Select a VM size page, in VM Size, select ***🆃 B2ms***, and then select **Select**.
<br>

On the Basics page, in Username, enter ***🆃 AzureAdmin***, and then in Password and Confirm password, enter ***🆃 Az!42311660!***.
<br>

In Public inbound ports, ensure that **Allow selected ports** is selected, and then in Select inbound ports, ensure that **RDP (3389)** is selected.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/ce2d807e-2d6c-4310-946e-6cec5773420c" height="80%" width="80%" alt="9"/><br />
<br>

On the Disks page, in OS disk type, select **Standard HDD**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/cd19298e-5a03-46d8-9f72-2768e56c71c6" height="80%" width="80%" alt="9"/><br />
<br>

On the Monitoring page, in Boot diagnostics, select **Disable**.
<br>

Select **Review + create**, review the virtual machine specifications, and then select **Create** to deploy the virtual machine.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/75b36a49-ed33-4bbc-8ca8-f5e966b4627f" height="80%" width="80%" alt="9"/><br />
<br>

<br>

<h2></h2>
<br>

On the Azure portal home page, select **Virtual machines**, and then select **webVM1**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/d80bf6ad-7357-46be-ab36-eef86f52696e" height="90%" width="90%" alt="9"/><br />
<br>

On the webVM1 resource menu, in Settings, select **Disks**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/65734f1d-86ec-4378-bff8-a089e885345b" height="50%" width="50%" alt="9"/><br />
<br>

On the Disks page, in OS disk, verify that there is one disk, and then in the Encryption column, verify that the value is set to **SSE with PMK**.
<br>

In Data disk, verify that there are no data disks.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/ebe999db-a36f-4046-b063-1f649e2b2aa7" height="100%" width="100%" alt="9"/><br />
<br>

<br>

  <details close> 
  
**<summary> 💡 Note</summary>**

 - **Server-Side Encryption (SSE)** of Azure Disk Storage is enabled by default and encrypts disks at the storage server level by using a Platform-Managed key (PMK).

 - The encryption key is managed automatically by the platform, in this case Azure, including protection and regular rotation.
 
 - You can use Server-Side Encryption with a customer-managed key (SSE with CMK) to manage the encryption key manually for compliance reasons.
 
 - You can combine SSE with Azure Disk Encryption (ADE), which additionally encrypts the disk at the OS level by using technologies such as BitLocker (Windows) or DM-Crypt (Linux), for what is called ***double encryption at rest*** high security requirements. 

  </details>

<br>


<br>
<br>

<h2>2️⃣ Add a new Data Disk to the Azure Virtual Machine</h2>
<br>

On the webVM1 Disks page, in Data disks, select **Create and attach a new disk**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/4e604b1f-4cde-48ba-824c-c70cc980bba1" height="100%" width="100%" alt="9"/><br />
<br>

In Disk name, enter ***🆃 DataFiles***, in Storage type, select **Standard HDD**, in Size (GiB), enter ***🆃 128***, and then on the command bar, select **Apply**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/ae381971-f3b6-491c-88f3-b1df2df57bf0" height="100%" width="100%" alt="9"/><br />
<br>

<br>

<h2></h2>
<br>

On the webVM1 Overview page, on the command bar, select **Connect**, and then under Native RDP, select **Select**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/128ac032-90e0-45c7-a59c-bb49cd00a9fb" height="70%" width="70%" alt="9"/><br />
<br>

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/b3071ef9-bb7b-4d71-a9b4-d8f9c183e227" height="70%" width="70%" alt="9"/><br />
<br>

On the Native RDP page, select **Download RDP File**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/57340571-9c9a-411e-bdea-871783b17bfb" height="60%" width="60%" alt="9"/><br />
<br>

Open the RDP file, and then in the Remote Desktop Connection window, select **Connect**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/761e25df-1f27-43ec-b126-8e332252198b" height="50%" width="50%" alt="9"/><br />
<br>

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/ab490c8f-f5c1-4df4-b0b0-2dfaec759e4e" height="60%" width="60%" alt="9"/><br />
<br>

When prompted for credentials, in User Name, enter ***🆃 AzureAdmin***, in Password, enter ***🆃 Az!42311660!***, and then select **OK**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/e9becc7b-dd30-47ae-9d91-2b2b0dadd0bc" height="60%" width="60%" alt="9"/><br />
<br>

In the Remote Desktop Connection warning message box, select **Yes**, and then wait for the RDP session to initialize.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/672ee134-8abc-445e-946f-d9632f542bba" height="60%" width="60%" alt="9"/><br />
<br>

In the RDP session, if prompted to allow your PC to be discoverable by other PCs and devices on this network, select **No**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/147de1cd-9efc-4162-ac1a-50ad42d72bfe" height="40%" width="40%" alt="9"/><br />
<br>

Wait for Server Manager to load, and then minimize **Server Manager**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/60dac6f3-7f26-4624-bf0e-d6cc5e3cd233" height="100%" width="100%" alt="9"/><br />
<br>

<br>

<h2></h2>
<br>

In the Remote Desktop Connection window, right-click **Start**, and then select **Disk Management**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/dd444014-2e32-46f3-90fe-291888c93bb4" height="40%" width="40%" alt="9"/><br />
<br>
  
In the Initialize Disk dialog box, review the default values, and then select **OK** to initialize the new disk.The Initialize Disk window
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/a4f89ba2-e018-467a-9869-a34b3f248e7e" height="80%" width="80%" alt="9"/><br />
<br>

In Disk Management, right-click the new, unallocated disk, and then select **New Simple Volume**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/52a607bb-4d8f-4435-8dfe-4aac7e0bf85b" height="80%" width="80%" alt="9"/><br />
<br>

In the New Simple Volume Wizard, select **Next** twice to advance to the Assign Drive Letter or Path page.
<br>

In Assign the following drive letter, ensure that F is selected, and then select **Next**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/18157522-9e84-4f44-9a4f-ad5f04667a9f" height="70%" width="70%" alt="9"/><br />
<br>

In File System, ensure that **NTFS** is selected, and then in Volume label, enter ***🆃 DataFiles***,
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/f0a2a549-776c-4976-a895-c2acff20ee29" height="70%" width="70%" alt="9"/><br />
<br>

Select **Next**, and then select **Finish** to format the new disk.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/e3bf4f1a-80fe-4d21-b789-9f59e37d0a0e" height="70%" width="70%" alt="9"/><br />
<br>

Close the **Disk Management** window.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/e24ef5ed-3d56-49f7-8ee5-81a18775a5a8" height="70%" width="70%" alt="9"/><br />
<br>

Then close the **Remote Desktop Connection** window.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Azure-Disk-Encryption/assets/172988970/d0f93c86-6eff-4da8-8f76-60956032a70a" height="100%" width="100%" alt="9"/><br />
<br>


<br>


<br>
<br>

<h2>3️⃣ Configure Peering Connections between the Virtual Networks</h2>
<br>
 
On the Azure portal home page, in the Search bar, search for and select webVNET to display the ***webVNET*** virtual network page.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/516d697e-5e68-4355-bc73-59c724b948ca" height="80%" width="80%" alt="9"/><br />
<br>

On the webVNET resource menu, in Settings, select **Peerings**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/d963ab25-143b-4ed2-973b-dab7bfe2c1ac" height="50%" width="50%" alt="9"/><br />
<br>

Then on the command bar, select **Add** to add a peering connection between the virtual networks.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/d3d74ed6-9eec-47ff-a1f3-98ed6d7043f9" height="50%" width="50%" alt="9"/><br />
<br>

On the Add peering page, in This virtual network, in Peering link name, enter ***🆃 webVNET-to-appVNET***.

In Remote virtual network, in Peering link name, enter ***🆃 appVNET-to-webVNET***, and then in Virtual network, select **appVNET**.

Select **Add**, and then wait for the peering connection to be created.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/fc27650f-9247-49a3-ac51-64ef679bb683" height="50%" width="50%" alt="9"/><br />

<br>
<h2></h2>
<br>

<h3>➡️ Verify that the webVNET-to-appVNET peering connection status is Connected</h3>
<br>

On the webVNET resource menu, in Settings, select **Peerings**.

On the Peerings page, in webVNET-to-appVNET, verify that the Peering status is **Connected** ✅

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/cf3a2150-bd07-4114-b14e-73d709c1f447" height="80%" width="80%" alt="9"/><br />

 <br>
<h2></h2>
<br>

<h3>➡️ Verify that the appVNET-to-webVNET peering connection status is Connected</h3>
<br>

On the webVNET - Peerings page, in webVNET-to-appVNET, in Peer, select **appVNET** to display the appVNET virtual network page.

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/1342638a-bf12-444a-bf09-7895103fb32e" height="80%" width="80%" alt="9"/><br />
<br>

On the appVNET resource menu, in Settings, select **Peerings**.

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/acf4fa7d-33c0-4f57-a5f1-3217d117028b" height="50%" width="50%" alt="9"/><br />
<br>

On the Peerings page, in appVNET-to-webVNET, verify that the Peering status is **Connected** ✅

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/60a8e0eb-b7ff-4b1d-a27a-bdd503f3d5a9" height="80%" width="80%" alt="9"/><br />
<br>

If the peering connection does not appear on the Peerings page, on the command bar, select **Refresh**.

<br>
<br>

<h2>Summary</h2>

Congratulations, you have completed the **Configure Virtual Network Connectivity by using Peering** Lab.

You have accomplished the following:

- Created a **Virtual Network for a Web Server Tier** by using the **Azure Portal**.

- Created a **Virtual Network for an Application Server Tier** by using **Azure CLI commands in Azure Cloud Shell**.

- Configured **Peering Connections** between the **Virtual Networks**.

<br>
<br>
<br>
<br>
