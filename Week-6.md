# Create an Internal & External Load balancer(Verify It’s working).

## Prerequisites
Ensure you have already created your virtual network (VNet), subnets, and deployed your VMs as outlined in the previous steps.

## 1. Create an External Load Balancer

### 1.1 Create the Load Balancer
1. Go to the Azure portal.
2. Navigate to "Create a resource" and select "Load Balancer".
3. Configure the load balancer:
   - **Name**: ExternalLB
   - **Type**: Public
   - **SKU**: Basic or Standard (depending on your needs)
   - **Virtual Network**: Select your existing VNet
   - **Subnet**: Select the Web Tier subnet
   - **Public IP address**: Create a new one or select an existing one

### 1.2 Configure Backend Pools
1. In the load balancer settings, select "Backend pools".
2. Add a new backend pool:
   - **Name**: WebBackendPool
   - **Add backend pool without a virtual machine scale set**: Yes
   - **Add**: Select the Web Tier VMs

### 1.3 Configure Health Probes
1. In the load balancer settings, select "Health probes".
2. Add a new health probe:
   - **Name**: HTTPProbe
   - **Protocol**: HTTP
   - **Port**: 80
   - **Path**: /

### 1.4 Configure Load Balancing Rules
1. In the load balancer settings, select "Load balancing rules".
2. Add a new rule:
   - **Name**: HTTPRule
   - **Frontend IP address**: Select the Public IP
   - **Backend pool**: Select WebBackendPool
   - **Protocol**: TCP
   - **Port**: 80
   - **Backend port**: 80
   - **Health probe**: Select HTTPProbe

### 1.5 Verify the External Load Balancer
1. Obtain the public IP address of the load balancer.
2. Open a web browser and navigate to the public IP address.
3. You should see the default Apache/IIS page served by one of the Web Tier VMs.

## 2. Create an Internal Load Balancer

### 2.1 Create the Load Balancer
1. Go to the Azure portal.
2. Navigate to "Create a resource" and select "Load Balancer".
3. Configure the load balancer:
   - **Name**: InternalLB
   - **Type**: Internal
   - **SKU**: Basic or Standard (depending on your needs)
   - **Virtual Network**: Select your existing VNet
   - **Subnet**: Select the App Tier subnet
   - **Private IP address**: Choose a static or dynamic address

### 2.2 Configure Backend Pools
1. In the load balancer settings, select "Backend pools".
2. Add a new backend pool:
   - **Name**: AppBackendPool
   - **Add backend pool without a virtual machine scale set**: Yes
   - **Add**: Select the App Tier VMs

### 2.3 Configure Health Probes
1. In the load balancer settings, select "Health probes".
2. Add a new health probe:
   - **Name**: HTTPProbe
   - **Protocol**: HTTP
   - **Port**: 80
   - **Path**: /

### 2.4 Configure Load Balancing Rules
1. In the load balancer settings, select "Load balancing rules".
2. Add a new rule:
   - **Name**: HTTPRule
   - **Frontend IP address**: Select the Private IP
   - **Backend pool**: Select AppBackendPool
   - **Protocol**: TCP
   - **Port**: 80
   - **Backend port**: 80
   - **Health probe**: Select HTTPProbe

### 2.5 Verify the Internal Load Balancer
1. Obtain the private IP address of the load balancer.
2. From one of the Web Tier VMs, open a web browser and navigate to the private IP address.
3. You should see the default Apache/IIS page served by one of the App Tier VMs.

## Summary
You have successfully created and verified both an internal and external load balancer. The external load balancer allows traffic from the internet to your Web Tier, while the internal load balancer manages traffic within your network, specifically from the Web Tier to the App Tier.
