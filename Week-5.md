# **Week-5: Setting Up Three-Tier Architecture in Azure with Network Security Groups (NSGs)**

---

### **Task:**  
Create a network infrastructure with three distinct tiers (Web, App, DB) in Azure. Configure communication rules between the tiers and set up internet access for only the Web tier. Deploy virtual machines (VMs) in each tier (both Linux and Windows), configure Apache on Linux VMs, and IIS on Windows VMs.

---

### **Answer:**  

#### **Overview of the Three-Tier Architecture:**
1. **Web Tier:**  
   This tier is responsible for receiving HTTP/HTTPS requests from the internet and forwarding them to the App tier.
   
2. **App Tier:**  
   This tier is responsible for processing requests from the Web tier and accessing the DB tier for data retrieval.
   
3. **DB Tier:**  
   This tier is responsible for handling database requests but does not communicate directly with the Web or App tiers, except through the App tier.

---

### **Step-by-Step Process:**

#### **Step 1: Create the Subnets**  
1. In the **Azure Portal**, create a new **Virtual Network** (VNet) and define three subnets:
   - **Web Tier Subnet**: For the Web servers (VMs).
   - **App Tier Subnet**: For the Application servers (VMs).
   - **DB Tier Subnet**: For the Database servers (VMs).

#### **Step 2: Configure Network Security Groups (NSGs)**  
Create **NSGs** to control the traffic flow between the tiers and to/from the internet.

##### **Web Tier NSG Configuration:**
- **Inbound Rules:**
  - Allow **HTTP (80)** and **HTTPS (443)** from the Internet (0.0.0.0/0).
  - Allow all traffic from the **App Tier Subnet**.
- **Outbound Rules:**
  - Allow all traffic to the **App Tier Subnet**.
  - Allow **HTTP (80)** and **HTTPS (443)** to the Internet.

##### **App Tier NSG Configuration:**
- **Inbound Rules:**
  - Allow all traffic from the **Web Tier Subnet**.
  - Allow all traffic from the **DB Tier Subnet**.
- **Outbound Rules:**
  - Allow all traffic to the **Web Tier Subnet**.
  - Allow all traffic to the **DB Tier Subnet**.

##### **DB Tier NSG Configuration:**
- **Inbound Rules:**
  - Allow all traffic from the **App Tier Subnet**.
- **Outbound Rules:**
  - Block all traffic to ensure it cannot communicate with Web and App tiers.

#### **Step 3: Deploy Virtual Machines (VMs) in Each Tier**  
Deploy two VMs in each subnet, one running Linux and the other running Windows.

##### **Web Tier VMs:**

1. **Linux VM (Ubuntu):**
   - Deploy a **Linux VM (Ubuntu)** in the **Web Tier Subnet**.
   - **Install Apache Server:**
     ```bash
     sudo apt update
     sudo apt install apache2 -y
     sudo systemctl start apache2
     sudo systemctl enable apache2
     ```

2. **Windows VM (Windows Server):**
   - Deploy a **Windows Server VM** in the **Web Tier Subnet**.
   - **Install IIS Server:**
     - Open **PowerShell** as Administrator and run:
     ```powershell
     Install-WindowsFeature -name Web-Server -IncludeManagementTools
     ```

##### **App Tier VMs:**

1. **Linux VM (Ubuntu):**
   - Deploy a **Linux VM (Ubuntu)** in the **App Tier Subnet**.
   - **Install Apache Server:**
     ```bash
     sudo apt update
     sudo apt install apache2 -y
     sudo systemctl start apache2
     sudo systemctl enable apache2
     ```

2. **Windows VM (Windows Server):**
   - Deploy a **Windows Server VM** in the **App Tier Subnet**.
   - **Install IIS Server:**
     - Open **PowerShell** as Administrator and run:
     ```powershell
     Install-WindowsFeature -name Web-Server -IncludeManagementTools
     ```

##### **DB Tier VMs:**

1. **Linux VM (Ubuntu):**
   - Deploy a **Linux VM (Ubuntu)** in the **DB Tier Subnet**.
   - **Install MySQL Server:**
     ```bash
     sudo apt update
     sudo apt install mysql-server -y
     sudo systemctl start mysql
     sudo systemctl enable mysql
     ```

2. **Windows VM (Windows Server):**
   - Deploy a **Windows Server VM** in the **DB Tier Subnet**.
   - **Install SQL Server:**
     - Follow the installation steps for **SQL Server** on Windows.

---

#### **Step 4: Additional Configuration and Testing**

1. **NSG Association:**  
   Ensure that the **Network Security Groups (NSGs)** are associated with the correct subnets for each tier (Web, App, DB).

2. **VM IP Address Configuration:**  
   Configure the VMs to use **internal IP addresses** for communication between them. This will prevent public IP addresses from being used for inter-tier communication.

3. **Communication Rules Between Tiers:**
   - The **Web tier** can communicate only with the **App tier** but not with the **DB tier**.
   - The **App tier** can communicate with both the **Web** and **DB** tiers.
   - The **DB tier** can only communicate with the **App tier**.

4. **Internet Access for Web Tier:**
   - Set up routing so that only the **Web tier** VMs have **internet access**.
   - Ensure that **App** and **DB tier** VMs do not have internet access.

5. **Test Connectivity Between VMs:**
   - **Ping Test:** Use **ping** to check the connectivity between VMs across the tiers.
   - **Web Tier Access:** From a Web VM, ensure it can connect to the App VM but not the DB VM.
   - **App Tier Access:** From an App VM, ensure it can connect to both Web and DB VMs.
   - **DB Tier Access:** From a DB VM, ensure it cannot connect to Web or App VMs.

---

### **Outcomes:**

1. **Successful Network Setup:**
   - Created three subnets: **Web**, **App**, and **DB**.
   - Configured appropriate **NSGs** to control traffic and enforce security policies between the tiers.

2. **Deployment of Virtual Machines:**
   - Deployed **two VMs** in each subnet (one Linux and one Windows) and ensured the proper configurations (Apache and IIS).

3. **Secure Communication:**
   - Ensured the Web tier can only communicate with the App tier, and the App tier can access both the Web and DB tiers.
   - Ensured that the DB tier can only communicate with the App tier.
   - Web tier VMs are the only ones allowed to connect to the internet.

4. **Testing & Validation:**
   - Verified communication between VMs across the tiers.
   - Ensured that the security settings for inbound and outbound traffic were correctly implemented.

---

### **Conclusion:**
The task demonstrates the configuration of a three-tier architecture with specific traffic control using **Network Security Groups (NSGs)** in Azure. The deployment of **Linux and Windows VMs** in each tier, along with proper web and database server configuration, ensures that the architecture is both functional and secure.

**Author: Dhaval Chhayla**
