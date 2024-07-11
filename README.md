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

You are a Security Engineer for an organization that needs you to enable **Azure Disk Encryption** on an **Azure Virtual Machine**.

<br>

1. First, you will **Create a Virtual Machine**.

2. Next, you will **Add a Data Disk to the Virtual Machine**.

4. Finally, you will **Enable Azure Disk Encryption**.

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

In Data disk, verify that there are no data disks.The current disk specifications in the Azure portal
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

<h2>2️⃣ Create a Virtual Network by using Azure Cloud Shell</h2>
<br>
 
In the Azure Portal, in the global controls, select the **Cloud Shell** icon.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/83d5df37-6cdb-4da2-8fa9-99a4fdb61607" height="80%" width="80%" alt="9"/><br />
<br>

In the Welcome to Azure Cloud Shell dialog box, select **Bash**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/56b65cb6-9732-45a0-abbe-ab0bdd5557d0" height="80%" width="80%" alt="9"/><br />
<br>

In the Getting started window, select **Mount storage account**, in Storage account subscription, select the existing **Challenge Labs** option, and then select **Apply**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/598c5ba9-9345-4c4a-9c3f-602c8ed9c580" height="80%" width="80%" alt="9"/><br />
<br>

In the Mount storage account window, select **I want to create a storage account**, and then select **Next**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/03d7e688-f940-451a-873f-c601cb059b02" height="80%" width="80%" alt="9"/><br />
<br>

In the Create storage account window, in Resource group, select **corp-datalod42226775**.

In Region, select **(US) East US**.

In Storage account name, enter ***🆃 cs42226775***.

In File share, enter ***🆃 cloudshell***, and then select **Create**.
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/81b26701-7e3a-4e31-96d1-ac2481276ecc" height="80%" width="80%" alt="9"/><br />
<br>

The Cloud Shell should take approximately 1–2 minutes to initialize.


✅ You will use this **Virtual Network** for the **Application Tier**.

<br>
<h2></h2>
<br>

In Azure Cloud Shell, run the following command to create a virtual network and subnet:

```commandline
az network vnet create --name appVNET --resource-group corp-datalod42226775 --address-prefix 10.20.0.0/16 --subnet-name app --subnet-prefix 10.20.0.0/25
```
<br>

⚠️ Cloud Shell does not support the keyboard shortcut Ctrl+V for paste.

- Instead, select the command prompt, and then use **Ctrl+Shift+V** to paste.

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/1633eed3-851a-4949-9c7e-f920217d3425" height="80%" width="80%" alt="9"/><br />
<br>

<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/eb66d335-b144-46bb-8adc-59ff15426181" height="80%" width="80%" alt="9"/><br />
<br>
<h2></h2>
<br>

Run the following command to verify the presence of a virtual network and subnet:

```commandline
az network vnet show --name appVNET --resource-group corp-datalod42226775
```
<br>
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/ce8116a3-778c-4113-abae-66448f272a19" height="80%" width="80%" alt="9"/><br />
<br>

The following screenshot shows the virtual network name and subnet name property values in the command output:
<p align="center">
<img src="https://github.com/franciscovfonseca/Configure-Virtual-Network-Connectivity-by-Using-Peering/assets/172988970/dd402600-f67e-4a8b-8f94-c5d917f0d207" height="80%" width="80%" alt="9"/><br />
<br>

Close the **Cloud Shell** window.

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
