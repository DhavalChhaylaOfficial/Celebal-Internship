# Week 3  

### **Task:**  
How to Create a Virtual Machine in a Virtual Network Using Azure?

---

### **Answer:**  

#### **Overview of Key Concepts**

1. **Virtual Machines (VMs):**  
   Virtual Machines mimic physical computers, enabling installation and execution of operating systems and software. They provide benefits like:  
   - Rapid provisioning  
   - Scalability  
   - Consolidation of multiple VMs on a single host  

2. **Virtual Networks (VNets):**  
   Virtual Networks ensure secure and isolated network environments. They allow:  
   - Segmentation into subnets  
   - Definition of IP address ranges  
   - Network connectivity between VMs and Azure services  

3. **Resource Groups:**  
   Logical containers to organize Azure resources. Benefits include:  
   - Simplified management  
   - Group-based policies and access controls  
   - Unified billing and lifecycle management  

---

### **Step-by-Step Process**

#### **Step 1: Create a Resource Group**  
1. Go to the Azure portal and click on "Create a resource" (+).  
2. Search for "Resource Group" and click "Create".  
3. Enter the details:  
   - **Subscription:** Select (e.g., Azure for Students).  
   - **Resource Group Name:** Provide a name (e.g., TestResourceGroup).  
   - **Region:** Choose a suitable region.  
4. Optionally add name-value key pairs.  
5. Review the information and click "Create".

---

#### **Step 2: Create a Virtual Network**  
1. In the Azure portal, create a Virtual Network and fill in the details:  
   - **Subscription:** Select the subscription.  
   - **Name:** Provide a name for the Virtual Network.  
   - **Region:** Choose the region.  
   - **Resource Group:** Select the previously created resource group.  
2. Define a subnet (e.g., TestSubnet) in the IP Addresses tab.  
3. Add optional tags in the Tags tab.  
4. Review the details and click "Create".  
5. Navigate to "Go to Resource" to confirm the Virtual Network is created.

---

#### **Step 3: Create a Virtual Machine**  
1. Go to the Virtual Machines dashboard in Azure and click "Create".  
2. In the Basics tab, provide the following details:  
   - **Subscription:** Select the subscription.  
   - **Resource Group:** Choose the previously created resource group.  
   - **Virtual Machine Name:** Provide a name (e.g., TestVirtualMachine).  
   - **Region:** Choose the deployment region.  
   - **Image:** Select the desired operating system.  
   - **Size:** Choose the compute and memory configuration.  
   - **Administrator Account:** Specify the username and password.  
3. Leave the remaining settings as default.  
4. Review the configuration in the "Review + Create" tab.  
5. Click "Create" to deploy the virtual machine.  
6. Navigate to "Go to Resource" to view the VM details.

---

### **Outcomes**  

- Successfully created a Virtual Machine within a Virtual Network in Azure.  
- Learned the integration of Virtual Machines, Virtual Networks, and Resource Groups to form a scalable and secure cloud infrastructure.  
- Enhanced knowledge of Azure's resource organization and deployment practices.  
- Realized the potential of cloud computing to achieve:  
  - **Scalability**  
  - **Flexibility**  
  - **Cost Optimization**  

**Conclusion:**  
This task demonstrated the foundational elements of cloud infrastructure, highlighting Azure's robust tools for creating and managing resources efficiently.
