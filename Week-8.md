# **Week-8: Configuration of On-Premises to Hub and Spoke Connectivity Using S2S Tunneling**

---

### **Task:**  
The task involves configuring on-premises to hub and spoke connectivity using Site-to-Site (S2S) tunneling from on-premises and hub-and-transit VNet peering from the hub to the spoke. You will configure Routing and Remote Access Service (RRAS) on the on-premises VM and establish S2S connectivity to the hub. The on-premises VM should be able to ping both the hub VM and the spoke VM successfully. The connectivity should be bi-directional, and there should be no direct connectivity between the spoke and the on-premises VNet.

---

### **Answer:**  

#### **Overview of Hub-and-Spoke Architecture:**
1. **Hub-and-Spoke Model:**
   - **Hub Network**: Centralized network where the routing and security policies are applied.
   - **Spoke Network**: Segmented network connected to the hub, but not directly to each other. 
   - **On-Premises Network**: External network connected to the Azure environment through the Site-to-Site VPN tunnel.

2. **Site-to-Site (S2S) VPN Tunnel:**  
   This type of VPN is used to securely connect the on-premises network to the hub in Azure. The on-premises network and the hub network will communicate over the VPN tunnel, allowing bi-directional traffic flow.

3. **RRAS on On-Premises VM:**  
   The Routing and Remote Access Service (RRAS) is configured on the on-premises VM to handle the routing of network traffic and establish the S2S VPN tunnel with the hub.

---

### **Step-by-Step Process:**

#### **Step 1: Configure the Virtual Network (VNet) in Azure**

1. **Navigate to Azure Portal:**  
   Go to the **Azure Portal**, click on **Create a resource**, and search for **Virtual Network**.

2. **Create Virtual Networks:**
   - **Hub VNet**:
     - **Name**: `Hub-VNet`
     - **Region**: Choose your preferred region
     - **Address Space**: `10.0.0.0/16`
     - **Subnets**: Create the necessary subnets, including `Hub-Subnet`.
   
   - **Spoke VNet**:
     - **Name**: `Spoke-VNet`
     - **Region**: Same as Hub VNet
     - **Address Space**: `10.1.0.0/16`
     - **Subnets**: Create necessary subnets, including `Spoke-Subnet`.

3. **Create the Hub-and-Spoke Peering:**
   - Navigate to the **Hub VNet** and select **Peering**.
   - Create a peering between the **Hub-VNet** and **Spoke-VNet** to allow traffic from the hub to the spoke.

4. **Create VPN Gateway for Hub VNet:**
   - Go to **Create a resource** → **VPN Gateway**.
   - **Name**: `Hub-VPN-Gateway`
   - **Type**: VPN
   - **SKU**: Choose Basic or Standard
   - **Virtual Network**: Select `Hub-VNet`
   - **Public IP Address**: Create a new public IP for the VPN gateway.

5. **Verify VNet Peering and VPN Gateway Creation:**
   After creating the virtual networks, verify that the VNet peering and VPN gateway have been successfully created.

---

#### **Step 2: Configure RRAS on On-Premises VM**

1. **Install RRAS Role on the On-Premises VM:**  
   - Log in to the on-premises VM and open **Server Manager**.
   - Go to **Manage** → **Add Roles and Features** → **Select RRAS**.
   - Install the **Remote Access** role with **Routing** and **VPN** options.

2. **Configure RRAS for VPN:**
   - Open the **RRAS Management Console**.
   - Right-click on the server name and select **Configure and Enable Routing and Remote Access**.
   - Select **Custom Configuration** and enable **VPN Access** and **LAN Routing**.

3. **Configure IPsec/IKE for Site-to-Site VPN:**
   - In the RRAS console, configure the **VPN Server** to accept connections using **IPsec**.
   - Define the shared key used for the S2S connection.
   
4. **Configure Routing:**
   - Add routing rules to allow traffic to flow from the on-premises network to the Azure hub.

---

#### **Step 3: Configure the Local Network Gateway in Azure**

1. **Create Local Network Gateway:**
   - Navigate to **Create a resource** → **Local Network Gateway**.
   - **Name**: `OnPremises-LNG`
   - **Public IP Address**: Enter the public IP address of your on-premises VPN device.
   - **Address Space**: Define the IP range of the on-premises network (e.g., `192.168.0.0/24`).

2. **Verify the Local Network Gateway Creation:**
   After the creation, verify that the Local Network Gateway is created and configured with the correct public IP and address space.

---

#### **Step 4: Create the Site-to-Site VPN Connection**

1. **Create VPN Connection:**
   - Go to the **Hub-VPN-Gateway** and select **Connections**.
   - **Name**: `OnPrem-S2S-Connection`
   - **Connection Type**: Site-to-Site (IPSec)
   - **Local Network Gateway**: Select the `OnPremises-LNG`.
   - **Shared Key**: Enter the shared key configured on both the on-premises VPN device and Azure VPN Gateway.

2. **Establish the VPN Tunnel:**  
   After creating the connection, the tunnel will automatically be established.

---

#### **Step 5: Test the Connectivity**

1. **Verify Bi-directional Connectivity:**  
   - From the on-premises VM, try to **ping** the hub VM (`10.0.0.4`) and spoke VM (`10.1.0.4`).
   - Verify that traffic can flow successfully in both directions.

2. **Check the Routing Tables:**  
   Ensure that the routing tables on the on-premises VM and in Azure are correctly configured to route traffic between the on-premises network, hub, and spoke networks.

---

### **Outcomes:**

- **On-Premises to Hub Connectivity:** Successfully established a Site-to-Site VPN connection between the on-premises network and the Azure Hub network.
- **Hub-to-Spoke Connectivity:** Enabled communication from the Hub VNet to the Spoke VNet via VNet peering.
- **Bi-directional Connectivity:** Verified that the on-premises VM can successfully ping both the Hub VM and the Spoke VM.
- **No Direct Connectivity Between Spoke and On-Premises VNet:** Ensured that there is no direct connectivity between the Spoke and the on-premises network, as intended.

---

### **Conclusion:**
You have successfully configured the **On-Premises to Hub and Spoke Connectivity** using **Site-to-Site (S2S) VPN tunneling**. The on-premises VM can securely communicate with both the Hub and the Spoke VMs, while the traffic between the Spoke and the On-Premises network is not directly established, ensuring a secure and segmented network.

**Author: Dhaval Chhayla**
