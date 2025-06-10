<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Domain Controller in Azure
- Create a Virtual Network and Subnet
- Setup Client in Azure
- Set Domain Controller as DNS Server
- Confirm Connection

<h1>Deployment and Configuration Steps</h1>

<h2>Domain Controller Setup in Azure</h2>
This guide walks you through creating a Resource Group, Virtual Network, Domain Controller VM, setting a static IP, and disabling the Windows Firewall for testing connectivity.</ br>


<p>
<img src="https://i.imgur.com/wmtjjzc.png" height="80%" width="80%" alt="Azure Portal Resourse Groups Page"/>
</p>
<p>

   ## Step 1: Create a Resource Group

- Log in to the [Azure Portal](https://portal.azure.com).
- In the left-hand menu, select **Resource groups**.
- Click **+ Create**.
- Enter a name for the resource group (e.g., `Capsule-Corp`).
- Choose a region (e.g., `East 2 US`).
- Click **Review + create** then **Create**.
</p>
<br />

<p>
<img src="https://i.imgur.com/QD29DmZ.png" height="80%" width="80%" alt="Azure Portal Virtual Network Creation Page"/>
</p>
<p>

   ## Step 2: Create a Virtual Network and Subnet

- In the Azure Portal, go to **Virtual networks**.
- Click **+ Create**.
- Select the previously created Resource Group.
- Enter a name for the virtual network (e.g., `CapsuleCorpIT-vm`).
- Choose the same region as your Resource Group.
- Set the **Address space** (e.g., `10.0.0.0/16`).
- Under **Subnets**, add a subnet:
   - Name: `CapsuleCSubnet`
   - Subnet address range: `10.0.1.0/24`
- Click **Review + create** then **Create**.
  
</p>
<br />

<p>
<img src="https://i.imgur.com/c7v9Vg2.png" height="80%" width="80%" alt="Azure VM Creation Wizard"/>
</p>
<p>

   ## Step 3: Create the Domain Controller VM (Windows Server 2022)

- Navigate to **Virtual machines** in Azure Portal.
- Click **+ Create** > **Azure virtual machine**.
- Select the Resource Group created earlier.
- Enter the VM name: `CapsuleCorpDC`.
- Select **Region** matching the Resource Group.
- For **Image**, select **Windows Server 2022 Datacenter: Azure Edition Hotpatch**.
- Choose a VM size (e.g., `Standard_B1s`).
- Set **Administrator account**:
   - Username: `CapsuleCorpAdmin`
   - Password: `TimeTravel92`
- Under **Networking**, select the previously created Virtual Network (`CapsuleCorpIT-vm-vnet`) and subnet (`CapsuleCSubnet`).
- Click **Review + create**, then **Create**.
  
</p>
<br />

<p>
<img src="https://i.imgur.com/E2JUo0c.png" height="80%" width="80%" alt="Azure Portal NIC IP Configuration Page"/>
</p>
<p>

   ## Step 4: Set the Domain Controller’s NIC Private IP Address to Static

- After the VM is deployed, go to **Virtual machines** and select `CapsuleCorpDC`.
- In the left menu, click **Networking** followed by **Network Settings**.
- Under **Network Interface**, click on the NIC name.
- Select **IP configurations**.
- Click on the IP configuration (usually named `ipconfig1`).
- Change **Private IP address assignment** from **Dynamic** to **Static**.
- Note or set the desired static private IP address (e.g., `10.0.1.4`).
- Click **Save**.
    
</p>
<br />

<p>
<img src="https://i.imgur.com/OVa40hN.png" height="80%" width="80%" alt="Windows Firewall Turned Off"/>
</p>
<p>

   ## Step 5: Log into the VM and Disable the Windows Firewall (For Testing)
   
- Use Remote Desktop (RDP) to connect to `DC-1` using:
   - Username: `CapsuleCorpAdmin`
   - Password: `TimeTravel92`
- Once logged in, right click the **Start Menu**
- Run **wf.msc** (Windows Firewall)
- Click **Windows Defender Firewall Properties**
   - Change Firewall State to **Off**
   - Click **Apply**, then **OK** 

</p>
<br />

<h2>Client Setup in Azure</h2>
This guide walks through the process of creating a Windows 10 client virtual machine, configuring its DNS settings to point to a Domain Controller (DC-1), and validating network connectivity.</ br>


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

   ## Step 1: Create the Client VM (Windows 10)

- In the [Azure Portal](https://portal.azure.com), go to **Virtual Machines**.
- Click **+ Create** > **Azure virtual machine**.
- Select the same **Resource Group** and **Region** as the Domain Controller.
- Enter the VM name: `Client-1`.
- For **Image**, select **Windows 10 Pro, version 22H2** or the latest available.
- Set **Username** to `labuser` and **Password** to `Cyberlab123!`.
- Under the **Networking** tab:
   - Choose the same **Virtual Network** and **Subnet** as `DC-1` (e.g., `LabVNet` and `LabSubnet`).
- Click **Review + create**, then **Create**.
   
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

   ## Step 2: Set Client VM’s DNS Settings to the Domain Controller’s Private IP Address

- Once deployed, go to **Virtual Machines** and select `Client-1`.
- In the **Networking** section, click the **Network Interface** name.
- Click **DNS Servers** under **Settings**.
- Choose **Custom** and input the **Private IP Address** of `DC-1` (e.g., `10.0.1.4`).
- Click **Save**.
   
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

   ## Step 3: Restart the Client VM

- From the Client VM overview page in the Azure Portal, click **Restart**.
- Wait until the VM finishes restarting and shows as **Running**.
   
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

   ## Step 4: Log into Client VM

- Use **Remote Desktop (RDP)** to connect to `Client-1`.
   - Use the credentials:
     - Username: `labuser`
     - Password: `Cyberlab123!`

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

   ## Step 5: Ping the Domain Controller's Private IP Address

- Open **Command Prompt** or **PowerShell** on the Client VM.
   - Type the following command: *ping 10.0.1.4*
- Confirm that the ping returns successful replies
   
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

   ## Step 6: Check DNS Settings via ipconfig /all

- On the Client VM, **open Powershell**.
   - Type the following command: *ipconfig /all*
- In the output, under the network adapter, look for the **DNS Servers** line.
- It should display the Private IP Address of the Domain Controller.

</p>
<br />
