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

<p>
<img src="https://i.imgur.com/wmtjjzc.png" height="80%" width="80%" alt="Azure Portal Resourse Groups Page"/>
</p>
<p>
# Step 1: Create a Resource Group

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

1. In the Azure Portal, go to **Virtual networks**.
2. Click **+ Create**.
3. Select the previously created Resource Group.
4. Enter a name for the virtual network (e.g., `CapsuleCNet`).
5. Choose the same region as your Resource Group.
6. Set the **Address space** (e.g., `10.0.0.0/16`).
7. Under **Subnets**, add a subnet:
   - Name: `CCSubnet`
   - Subnet address range: `10.0.1.0/24`
8. Click **Review + create** then **Create**.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Azure VM Creation Wizard"/>
</p>
<p>
## Step 3: Create the Domain Controller VM (Windows Server 2022)

1. Navigate to **Virtual machines** in Azure Portal.
2. Click **+ Create** > **Azure virtual machine**.
3. Select the Resource Group created earlier.
4. Enter the VM name: `DC-1`.
5. Select **Region** matching the Resource Group.
6. For **Image**, select **Windows Server 2022 Datacenter**.
7. Choose a VM size (e.g., `Standard B2ms`).
8. Set **Administrator account**:
   - Username: `labuser`
   - Password: `Cyberlab123!`
9. Under **Networking**, select the previously created Virtual Network (`LabVNet`) and subnet (`LabSubnet`).
10. Click **Review + create**, then **Create**.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />



<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
