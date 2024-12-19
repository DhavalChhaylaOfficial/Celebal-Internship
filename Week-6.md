# **Week-6: Create an Internal & External Load Balancer in Azure**

---

### **Task:**  
Create both an internal and an external load balancer in Azure to manage traffic. Ensure they are correctly configured and verified to balance traffic across multiple Virtual Machines (VMs).

---

### **Answer:**  

#### **Overview of Load Balancers:**
1. **External Load Balancer:**  
   This load balancer is used to distribute incoming internet traffic to the Web Tier VMs. It is publicly accessible and serves as the entry point for external requests.

2. **Internal Load Balancer:**  
   The internal load balancer is used to distribute traffic within the internal network. It manages traffic from the Web Tier to the App Tier without exposing the App Tier VMs to the internet.

---

### **Step-by-Step Process:**

#### **Step 1: Create the External Load Balancer**

1. **Navigate to Azure Portal:**  
   Go to the **Azure Portal**, and click on **Create a resource**.
   
2. **Create Load Balancer:**
   - Select **Load Balancer** from the resources list.
   - **Name**: ExternalLB
   - **Type**: Public
   - **SKU**: Basic or Standard (based on your requirements)
   - **Virtual Network**: Select your existing VNet
   - **Subnet**: Choose the **Web Tier Subnet**
   - **Public IP Address**: Create a new public IP or select an existing one.

3. **Configure Backend Pools:**
   - Under the Load Balancer settings, go to **Backend Pools**.
   - **Name**: WebBackendPool
   - **Backend Pool without a Virtual Machine Scale Set**: Yes
   - **Add VMs**: Select the VMs in your **Web Tier** subnet.

4. **Configure Health Probes:**
   - Go to **Health Probes** in the settings.
   - **Name**: HTTPProbe
   - **Protocol**: HTTP
   - **Port**: 80
   - **Path**: /

5. **Configure Load Balancing Rules:**
   - Under **Load Balancing Rules**, click on **Add**.
   - **Name**: HTTPRule
   - **Frontend IP Address**: Select the **Public IP**
   - **Backend Pool**: Select **WebBackendPool**
   - **Protocol**: TCP
   - **Port**: 80
   - **Backend Port**: 80
   - **Health Probe**: Select **HTTPProbe**

6. **Verify the External Load Balancer:**
   - Obtain the public IP address of the load balancer.
   - Open a web browser and navigate to the public IP address.
   - You should see the default Apache/IIS page served by one of the Web Tier VMs.

---

#### **Step 2: Create the Internal Load Balancer**

1. **Navigate to Azure Portal:**
   Go to **Azure Portal** and select **Create a resource**.

2. **Create Load Balancer:**
   - Select **Load Balancer** from the list of available resources.
   - **Name**: InternalLB
   - **Type**: Internal
   - **SKU**: Basic or Standard (based on your requirements)
   - **Virtual Network**: Select your existing VNet
   - **Subnet**: Choose the **App Tier Subnet**
   - **Private IP Address**: Select **Static** or **Dynamic IP**.

3. **Configure Backend Pools:**
   - In the Load Balancer settings, go to **Backend Pools**.
   - **Name**: AppBackendPool
   - **Add Backend Pool without a Virtual Machine Scale Set**: Yes
   - **Add VMs**: Select the VMs in your **App Tier** subnet.

4. **Configure Health Probes:**
   - Go to **Health Probes** and add a new probe.
   - **Name**: HTTPProbe
   - **Protocol**: HTTP
   - **Port**: 80
   - **Path**: /

5. **Configure Load Balancing Rules:**
   - Go to **Load Balancing Rules** and click on **Add**.
   - **Name**: HTTPRule
   - **Frontend IP Address**: Select the **Private IP**
   - **Backend Pool**: Select **AppBackendPool**
   - **Protocol**: TCP
   - **Port**: 80
   - **Backend Port**: 80
   - **Health Probe**: Select **HTTPProbe**

6. **Verify the Internal Load Balancer:**
   - Obtain the private IP address of the load balancer.
   - From one of the **Web Tier VMs**, open a web browser and navigate to the private IP address.
   - You should see the default Apache/IIS page served by one of the **App Tier VMs**.

---

### **Outcomes:**

- **Load Balancer Setup:** Create and configure both **external** and **internal** load balancers in Azure for traffic distribution.
- **Traffic Distribution:** Distribute traffic efficiently to ensure **high availability** and **fault tolerance**.
- **IP Usage:** Understand the use of **public** and **private IPs** for external and internal communication.
- **Health Probes:** Set up **health probes** to monitor backend VM status and maintain reliability.
- **Verification:** Test and verify that load balancers are routing traffic correctly to VMs.


---

### **Conclusion:**
You have configured and verified both an **Internal** and **External Load Balancer** in Azure. The external load balancer manages incoming internet traffic to the Web Tier, while the internal load balancer ensures secure communication between the Web and App Tiers. This setup provides a scalable and secure infrastructure for your application.

**Author: Dhaval Chhayla**
