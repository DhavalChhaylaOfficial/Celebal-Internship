# **Week 3: Virtual Machine**

---

### **Task:**  
How to create and deploy a Virtual Machine (VM) within a Virtual Network (VNet) using Azure while leveraging resource management best practices?

---

### **Answer:**  

#### **Overview of Key Concepts**  

1. **Virtual Machines (VMs):**  
   VMs replicate physical computers, allowing installation and execution of operating systems and applications.  
   **Advantages:**  
   - Quick provisioning  
   - Scalability  
   - Cost-effective consolidation of resources  

2. **Virtual Networks (VNets):**  
   VNets provide secure, isolated environments for connecting VMs and Azure services.  
   **Key Features:**  
   - IP address management  
   - Subnet segmentation  
   - Hybrid connectivity options  

3. **Resource Groups:**  
   Logical containers for organizing Azure resources, simplifying lifecycle management.  
   **Benefits:**  
   - Simplified access control  
   - Unified billing and management  
   - Streamlined deployment processes  

---

### **Step-by-Step Process**  

#### **Step 1: Create a Resource Group**  
1. Log in to the **Azure Portal** and click on "Create a Resource".  
2. Search for and select **Resource Group**.  
3. Enter the details:  
   - **Subscription:** Choose an active subscription (e.g., Azure for Students).  
   - **Name:** Provide a unique resource group name (e.g., TestResourceGroup).  
   - **Region:** Select a data center region (e.g., East US).  
4. (Optional) Add tags for categorization.  
5. Click **Create** and confirm resource group creation.

---

#### **Step 2: Set Up a Virtual Network (VNet)**  
1. Navigate to "Create a Resource" and search for **Virtual Network**.  
2. Enter the following details:  
   - **Name:** Assign a name to the network (e.g., TestVNet).  
   - **Region:** Choose the same region as the resource group.  
   - **Resource Group:** Select the previously created resource group.  
3. Under the **IP Addresses** tab:  
   - Configure the address space and subnets (e.g., Subnet: TestSubnet).  
4. (Optional) Add tags for organization.  
5. Review and click **Create**.  

---

#### **Step 3: Create a Virtual Machine (VM)**  
1. Go to the **Virtual Machines** section in the Azure Portal and click on **Create**.  
2. Under the **Basics** tab:  
   - **Subscription:** Select the subscription.  
   - **Resource Group:** Choose the resource group.  
   - **VM Name:** Provide a VM name (e.g., TestVM).  
   - **Region:** Ensure it matches the VNet region.  
   - **Image:** Select the operating system (e.g., Ubuntu Server).  
   - **Size:** Configure the VM’s CPU and memory.  
   - **Authentication:** Define admin credentials (username and password).  
3. In the **Networking** tab:  
   - Connect the VM to the previously created Virtual Network and subnet.  
4. Leave default settings in the remaining tabs.  
5. Review configurations and click **Create**.  
6. After deployment, access the VM through the Azure portal or SSH.

---

### **Outcomes**  

1. **Infrastructure Creation:**  
   - Successfully deployed a Virtual Machine connected to a secure Virtual Network.  

2. **Practical Knowledge Gained:**  
   - Understood the role of resource groups for efficient management.  
   - Learned to configure IP ranges and subnets within Virtual Networks.  
   - Mastered VM setup and integration with VNets for seamless communication.  

3. **Cloud Benefits:**  
   - **Scalability:** Rapid deployment of additional VMs.  
   - **Security:** Isolated and manageable network configurations.  
   - **Cost Efficiency:** Pay-as-you-go model for optimized expenses.  

---

### **Conclusion**  

This task demonstrated the power of Azure for deploying secure, scalable cloud infrastructures. By integrating Virtual Machines with Virtual Networks and Resource Groups, it highlighted Azure’s flexibility and ease of resource management.  

**Author: Dhaval Chhayla**   
