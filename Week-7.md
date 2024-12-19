# **Week-7: Create Site-to-Site VPN Peering in Azure**

---

### **Task:**  
Create a Site-to-Site VPN connection in Azure to securely connect an on-premises network to an Azure Virtual Network (VNet). This includes setting up the virtual network, VPN gateway, and local network gateway to enable secure traffic flow between both environments.

---

### **Answer:**  

#### **Overview of Site-to-Site VPN:**
A Site-to-Site VPN connection is used to securely connect an on-premises network to an Azure virtual network over an IPsec/IKE (IKEv1 or IKEv2) VPN tunnel. It is ideal for connecting an on-premises data center or branch office network to Azure securely.

1. **Azure VPN Gateway:**  
   The VPN Gateway in Azure is used to connect to on-premises networks over the VPN tunnel.
   
2. **Local Network Gateway:**  
   The Local Network Gateway represents your on-premises VPN device and is used to define the address space of the on-premises network.

3. **Site-to-Site VPN Tunnel:**  
   The tunnel is the encrypted connection established between Azure and the on-premises network.

---

### **Step-by-Step Process:**

#### **Step 1: Create a Virtual Network in Azure**

1. **Navigate to Azure Portal:**  
   Go to the **Azure Portal**, click on **Create a resource**, and search for **Virtual Network**.

2. **Create Virtual Network:**
   - **Name**: `AZ-Vnet`
   - **Region**: Select a region
   - **Address Space**: Define a valid IP address range, e.g., `10.0.0.0/16`
   - **Subnet**: Create a subnet for the VPN Gateway named `GatewaySubnet`.

3. **Verify the Virtual Network Creation:**  
   After creation, go to the **Overview** of the virtual network to confirm that the subnet `GatewaySubnet` has been created.

---

#### **Step 2: Create the Virtual Network Gateway**

1. **Navigate to Azure Portal and Create VPN Gateway:**
   - **Name**: `VNG`
   - **Type**: VPN
   - **SKU**: Basic or Standard based on needs
   - **Virtual Network**: Select the `AZ-Vnet`
   - **Public IP Address**: Create a new public IP for the gateway

2. **Review and Create:**  
   Review your settings and click on **Create** to deploy the Virtual Network Gateway.

---

#### **Step 3: Create the Local Network Gateway**

1. **Navigate to Azure Portal:**  
   Click on **Create a resource**, and search for **Local Network Gateway**.

2. **Configure Local Network Gateway:**
   - **Name**: `LNG`
   - **Public IP Address**: Enter the public IP of your on-premises VPN device
   - **Address Space**: Define the IP range of the on-premises network, e.g., `192.168.0.0/24`

3. **Create the Local Network Gateway:**  
   After filling in the necessary details, click on **Create**.

---

#### **Step 4: Create the Site-to-Site Connection**

1. **Navigate to the VPN Gateway:**  
   Go to your created `VNG` and click on **Connections**.

2. **Create the Connection:**
   - **Name**: `S2SConnection`
   - **Connection Type**: Site-to-Site (IPSec)
   - **Virtual Network Gateway**: Select `VNG`
   - **Local Network Gateway**: Select `LNG`
   - **Shared Key**: Define a secure shared key for the VPN connection.

3. **Create the Connection:**  
   Click **OK** to establish the VPN tunnel.

---

#### **Step 5: Configure the On-Premises VPN Device**

1. **Configure IPsec/IKE Settings:**  
   On the on-premises VPN device, configure the VPN tunnel with the public IP of the `VNG` and the shared key.

2. **Verify VPN Tunnel Status:**  
   Ensure the VPN tunnel is established and active.

---

#### **Step 6: Test the VPN Connection**

1. **Verify the Connection:**  
   Test the connection by pinging from an on-premises device to a resource in the Azure virtual network.

2. **Check Logs for Errors:**  
   Monitor the connection status in both Azure and the on-premises device to troubleshoot any issues.

---

### **Outcomes:**

- **Site-to-Site VPN Connection:** Successfully created a secure Site-to-Site VPN connection between an Azure VNet and an on-premises network.
- **Network Connectivity:** Enabled secure communication between Azure and on-premises resources.
- **Public & Private IP Configuration:** Properly configured both public and private IP addresses for secure and reliable connections.
- **Testing & Verification:** Verified that traffic flows correctly between the two networks using the VPN tunnel.

---

### **Conclusion:**
You have successfully created a **Site-to-Site VPN peering** between an Azure Virtual Network and an on-premises network. This allows secure communication across both networks and is ideal for scenarios where hybrid cloud setups are required.

**Author: Dhaval Chhayla**
