# Create three subnets : 1. Web tier 2. App tier 3. DB tier <br> DB Tier should not access any tier(Web & App tier) App tier should access the DB tier and Web tier as well, Web tier should acccess only App tier. <br> Only Web tier is allowed to connect to the internet.Deploy two VM's in each tier(One VM should be Linux & another should be Windows). <br> Configure Apache Server on Linux VM's And IIS Server on Windows.

## 1. Create the Subnets
Create the following subnets in your virtual network (VNet):

- **Web Tier Subnet**
- **App Tier Subnet**
- **DB Tier Subnet**

## 2. Configure Network Security Groups (NSGs)
Create and configure NSGs to control the traffic between the subnets and to/from the internet.

### Web Tier NSG
- **Inbound rules:**
  - Allow HTTP/HTTPS from the Internet
  - Allow all traffic from App Tier subnet
- **Outbound rules:**
  - Allow all traffic to App Tier subnet
  - Allow HTTP/HTTPS to the Internet

### App Tier NSG
- **Inbound rules:**
  - Allow all traffic from Web Tier subnet
  - Allow all traffic from DB Tier subnet
- **Outbound rules:**
  - Allow all traffic to Web Tier subnet
  - Allow all traffic to DB Tier subnet

### DB Tier NSG
- **Inbound rules:**
  - Allow all traffic from App Tier subnet
- **Outbound rules:**
  - Block all traffic

## 3. Deploy Virtual Machines
Deploy two VMs in each subnet (one Linux and one Windows).

### Web Tier
#### Linux VM
1. Deploy a Linux VM (e.g., Ubuntu)
2. Install Apache Server:
    ```bash
    sudo apt update
    sudo apt install apache2 -y
    sudo systemctl start apache2
    sudo systemctl enable apache2
    ```

#### Windows VM
1. Deploy a Windows Server VM
2. Install IIS Server:
    - Open PowerShell as Administrator and run:
    ```powershell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```

### App Tier
#### Linux VM
1. Deploy a Linux VM (e.g., Ubuntu)
2. Install Apache Server:
    ```bash
    sudo apt update
    sudo apt install apache2 -y
    sudo systemctl start apache2
    sudo systemctl enable apache2
    ```

#### Windows VM
1. Deploy a Windows Server VM
2. Install IIS Server:
    - Open PowerShell as Administrator and run:
    ```powershell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```

### DB Tier
#### Linux VM
1. Deploy a Linux VM (e.g., Ubuntu)
2. Install MySQL Server:
    ```bash
    sudo apt update
    sudo apt install mysql-server -y
    sudo systemctl start mysql
    sudo systemctl enable mysql
    ```

#### Windows VM
1. Deploy a Windows Server VM
2. Install SQL Server:
    - Follow SQL Server installation steps.

## 4. Additional Configuration
- Ensure NSGs are associated with the appropriate subnets.
- Configure VMs to use internal IP addresses for communication.
- Ensure DB tier VMs accept traffic only from the App tier VMs.
- Ensure Web tier VMs communicate with App tier VMs but not directly with DB tier VMs.
- Ensure App tier VMs communicate with both Web and DB tier VMs.
- Set up routing so only the Web tier has internet access.
