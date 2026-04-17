# VPC Peering (Step by Step Guide)

---

### **Step 1: Objective** 
**What you do:** Review the lab goal.  
**Explanation:** The assignment is to implement **VPC Peering** so the Marketing, Developer, and Finance departments can communicate privately. All VPCs are private (no public internet access). You will create 3 VPCs, launch EC2 instances inside them, peer the VPCs, configure routes & security groups, and test connectivity using EC2 Instance Connect.

<img width="1207" height="679" alt="image" src="https://github.com/user-attachments/assets/08e24ba7-06d1-414d-be25-8757c872291c" />

---

### **Step 2: Search for VPC** 
**What you do:**  
1. Click the search bar at the top of the AWS Console.  
2. Type `VPC` and click **VPC**.  
**Explanation:** This opens the VPC service dashboard where you will create and manage all networks.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/65dbafd2-f50e-4a52-9e72-b21fbc19d3d8" />

---

### **Step 3: Click "Create VPC"** 
**What you do:** In the VPC dashboard, click the orange **Create VPC** button.  
**Explanation:** Starts the wizard to build your first VPC (Finance).

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/a6a5a5db-f4ff-4859-93d3-c89b6de98153" />

---

### **Step 4: Name tag** 
**What you do:** In the “Name tag auto-generation” field, type `Finance` (or click to edit).  
**Explanation:** Gives your VPC a friendly name so it’s easy to identify later.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/019c70c2-25f2-4594-82ce-da87d1282cf5" />

---

### **Step 5: IPv4 CIDR block** 
**What you do:** Under IPv4 CIDR block, keep the default `10.0.0.0/16` (or customize if needed).  
**Explanation:** Defines the private IP address range for this VPC. Finance uses `10.0.0.0/16`.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/97f7d94d-34a1-4a0f-965f-9ef61d39740e" />

---

### **Step 6: IPv6 CIDR block** 
**What you do:** Leave **No IPv6 CIDR block** selected.  
**Explanation:** The lab only needs IPv4. IPv6 is optional and not required here.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/cb8b3e57-a0c2-4e56-a419-1f792b1740ef" />

---

### **Step 7: Availability Zones** 
**What you do:** Choose **2 Availability Zones** (AZs).  
**Explanation:** Spreads resources across two data centers for high availability.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/ea21d1fa-c72e-4c66-98a9-499ce1646e06" />

---

### **Step 8: Public Subnet** 
**What you do:** Set **Number of public subnets** to **0**.  
**Explanation:** Finance VPC must be completely private, no internet-facing resources.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/9c6a5128-4a80-4a62-bc6c-9d7589523b6c" />

---

### **Step 9: Private Subnets** 
**What you do:** Set **Number of private subnets** to **2**.  
**Explanation:** Creates two private subnets (one per AZ) for your EC2 instances.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/c3476195-098a-4248-b6a5-5b8821fabacc" />

---

### **Step 10: Customize Subnets CIDR blocks** 
**What you do:** (Optional) Click “Customize subnets CIDR blocks” if you want to change the subnet ranges.  
**Explanation:** Used in later VPCs. For Finance, defaults are fine.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/5c3d3297-a223-4954-bdfa-397b28d25cca" />

---

### **Step 11: NAT Gateways** 
**What you do:** Choose **None**.  
**Explanation:** No need for internet outbound traffic in this basic lab.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/2598bcf7-13f8-4180-bb08-eff331ee97f5" />

---

### **Step 12: Create VPC** 
**What you do:**  
- Leave **S3 Gateway** and DNS options checked.  
- Click **Create VPC**.  
**Explanation:** Finalizes and launches the Finance VPC.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/96961a52-2ff9-45d2-bf88-5601b3cc4316" />

---

### **Step 13: Finance VPC created** 
**What you see:** Confirmation that Finance VPC is ready.  
**Explanation:** Now repeat the process for the other two departments.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/a7570eda-7850-43cd-a2ee-57f6c79d351c" />

---

### **Step 14: Create 2 more VPCs** 
**What you do:** Create **Marketing-vpc** and **Developer-vpc** using different CIDR blocks (e.g., `172.16.0.0/16` and `192.168.0.0/16`).  
**Explanation:** You now have three isolated VPCs.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/869384b4-f312-4f15-9330-1a3e71b846e4" />

---

### **Step 15: EC2 Instances** 
**What you do:** Search for **EC2** and select it.  
**Explanation:** Move to the EC2 console to launch servers.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/0008998d-67ee-4e3f-aaa9-99bcd3aad6ec" />

---

### **Step 16: Launch EC2 instance** 
**What you do:** Click **Launch instance**.  
**Explanation:** Starts the wizard to create your first EC2 server.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/5289e885-c12d-4944-ab3c-c6a549a00c65" />

---

### **Step 17: Name and tags** 
**What you do:** Name the instance (e.g., `finance-server`).  
**Explanation:** Easy identification.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/8d83ea3a-0ee2-4bdf-8304-0fe04d3ccf1f" />

---

### **Step 18: Amazon Machine Image (AMI)** 
**What you do:** Choose **Amazon Linux**.  
**Explanation:** Free, lightweight Linux OS provided by AWS.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/6a5929b1-993b-444a-a0c9-1585ebd0a755" />

---

### **Step 19: Instance Type** 
**What you do:** Select **t3.micro**.  
**Explanation:** free-tier eligible instance.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/234a27e7-d4fa-4279-af8d-61a729de005b" />

---

### **Step 20: Key Pair** 
**What you do:** Proceed without a key pair.  
**Explanation:** Simplifies the lab no need to download .pem files.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/c442afc5-6ce7-4d29-91ad-401d696d4cc0" />

---

### **Step 21: Edit the Network Settings** 
**What you do:** Click the **Edit** button under Network settings.  
**Explanation:** You will now assign the correct VPC and subnet.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/f6522247-4ee5-41d1-8bbb-b4bcc840b617" />

---

### **Step 22: Network Settings – VPC** 
**What you do:** Select the correct VPC for this instance (e.g., Finance-vpc).  
**Explanation:** Places the instance inside the right network.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/3156a14b-14e1-4962-a36f-c5535b9d0b72" />

---

### **Step 23: Network Settings – Subnet** 
**What you do:** Choose a private subnet in your preferred AZ.  
**Explanation:** Ensures the instance is in a private subnet.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/372587dd-bce0-4b48-8470-b53397527b4b" />

---

### **Step 24: Network Settings – Disable Auto-assign Public IP** 
**What you do:** Set **Auto-assign Public IP** to **Disable**.  
**Explanation:** Keeps the instance completely private.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/43916230-956f-481b-a7fd-adda823d2e67" />

---

### **Step 25: Network Settings – Select existing security group** 
**What you do:** Choose **Select existing security group** (we will edit it later).  
**Explanation:** Allows custom firewall rules later.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/a9227f96-b851-42eb-809d-78c5a1be1005" />

---

### **Step 26: Storage Settings** 
**What you do:** Leave default (8 GiB gp3).  
**Explanation:** Sufficient for this lab.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/24f4a0ae-0071-4a1d-b711-19e07a5be603" />

---

### **Step 27: Launch Instance** 
**What you do:** Click **Launch instance**.  
**Explanation:** Creates the server. Repeat steps 16–27 for the other two instances (`marketing-server` and `developer-server`).

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/8644db1d-bee2-4cd3-be03-03061d7cc93a" />

---

### **Step 28: Created 2 more Instances** 
**What you see:** All three instances are now running.  
**Explanation:** You now have one server in each VPC.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/3977ec0e-c871-4237-ac9f-ed52cf7588f4" />

---

### **Step 29: VPC Peering** 
**What you do:** In the VPC console, go to **Peering connections**.  
**Explanation:** VPCs are isolated by default, peering connects them privately.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/39f02673-7b1b-4742-94dc-ffde5cfbc558" />

---

### **Step 30: Click "Create peering connection"** 
**What you do:** Click the orange **Create peering connection** button.  
**Explanation:** Starts the peering wizard.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/47013ab6-13df-4b51-a73b-6a9448ef5363" />

---

### **Step 31: Name & Requester ID** 
**What you do:**  
- Name the connection (e.g., `marketing-finance`).  
- Select the Requester VPC (Marketing).  
**Explanation:** Marketing is requesting to connect to Finance.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/3fcde057-adb2-4470-bc55-71d4c30eee60" />

---

### **Step 32: Accepter ID** 
**What you do:** Select the Accepter VPC (Finance) → Click **Create peering connection**.  
**Explanation:** Finance will accept the request.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/410738e7-cc20-4ebb-bfb0-0eb8e9fb763e" />

---

### **Step 33: Click "Actions"** 
**What you do:** On the Finance side, select the request → **Actions → Accept request**.  
**Explanation:** Authorizes the peering.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/f2a607ce-79dc-4d4e-8cb1-fcf222c1bf8a" />

---

### **Step 34: Accept Request pop-up** 
**What you do:** Confirm and click **Accept request**.  
**Explanation:** Peering is now active. Repeat for Developer ↔ Finance.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/965d0d45-60ac-4517-9521-27813189968e" />

---

### **Step 35: Marketing and Developer VPCs peered to Finance** 
**What you see:** Two active peering connections.  
**Explanation:** All three VPCs are now linked.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/f3c85e69-8285-44dd-a4e3-da0d31d13681" />

---

### **Step 36: Creating Routes and Security Groups** 
**What you do:** Search for **EC2** again.  
**Explanation:** Next phase, allow traffic (security groups) and tell the network where to send packets (routes).

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/0a8df0db-3cdd-40ac-9bfd-09b70d83b064" />

---

### **Step 37: Security details** 
**What you do:** Select an instance → **Security** tab → Click the security group link.  
**Explanation:** Opens the firewall rules for editing.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/d3bb6fbc-d2a0-4525-b308-8c0919beb473" />

---

### **Step 38: Security group link** 
**What you do:** Scroll down and click the security group ID link.  
**Explanation:** Takes you to the security group management page.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/bfb8c439-e188-4a6f-b5af-941d3aafeb68" />

---

### **Step 39: Inbound rules** 
**What you do:** Click **Inbound rules** → **Edit inbound rules**.  
**Explanation:** You will now allow traffic from the other VPCs.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/372ad8b8-61ca-48d0-9c92-5345e635ea08" />

---

### **Step 40: Edit inbound rules** 
**What you do:**  
- Add rules allowing **All traffic** (or ICMP/SSH) from the other two VPC CIDRs.  
- Save rules.  
**Explanation:** This is the firewall permission. Repeat for all three security groups.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/a40a7b4f-84ac-4b2a-a74d-fe3e10982507" />

---

### **Step 41: Adding Routes** 
**What you do:** Go back to **Instances** list → Click the Finance instance.  
**Explanation:** Now configure routing tables.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/571004cb-25d3-4758-88cd-8c43e1ce3784" />

---

### **Step 42: Click Networking** 
**What you do:** Under **Networking**, click the **Subnet ID** link.  
**Explanation:** Goes to the subnet details.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/357ee66f-cdd2-4870-9a46-b423f461f3c2" />

---

### **Step 43: Subnets New page** 
**What you do:** Click the **Route table** link.  
**Explanation:** Opens the route table associated with the subnet.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/8dc10af8-3ddb-42cd-82c5-8acde1ed63c2" />

---

### **Step 44: Route tables** 
**What you do:** Click **Routes** → **Edit routes**.  
**Explanation:** Ready to add new routes.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/93d6a473-8e52-4f98-a6e2-3b77b1e9ad05" />

---

### **Step 45: Click "Edit Routes and Save changes"** 
**What you do:**  
- Click **Add route**.  
- Destination = other VPC CIDR (e.g., `172.16.0.0/16`).  
- Target = the peering connection ID.  
- Repeat for the third VPC.  
- Save changes.  
**Explanation:** Tells the VPC “send traffic for Marketing/Developer to the peering connection”. Repeat for every subnet in all three VPCs.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/0108bc38-1127-4d49-920c-10fbc5e9e8d1" />

---

### **Step 46: Test Connectivity** 
**What you do:** Select an instance (e.g., developer-server) → Click **Connect**.  
**Explanation:** Time to verify everything works.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/7bdb6ec2-8056-4660-ac5e-e2d072cfd830" />

---

### **Step 47: EC2 Instance Connect** 
**What you do:** Choose **EC2 Instance Connect** → Select **Connect using a Private IP**.  
**Explanation:** Browser-based SSH without public IP.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/b51b2a70-ab85-4abd-bfab-01caa832b446" />

---

### **Step 48: EC2 Instance Connect (Create Endpoint)** 
**What you do:** Click **Create EC2 Instance Connect Endpoint**.  
**Explanation:** Required for private IP connectivity.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/9406e583-4f55-41cf-96fc-d76b32a75650" />

---

### **Step 49: EC2 Instance Connect – Subnet** 
**What you do:** Select the subnet where your instance lives.  
**Explanation:** The endpoint must be in the same VPC/subnet.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/97c95faf-815f-44a8-a85a-16e3089a7190" />

---

### **Step 50: EC2 Instance Connect – Security Group** 
**What you do:** Select the security group you created earlier.  
**Explanation:** Allows the endpoint to reach the instance.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/32447b57-6263-446c-8be5-94149a077af0" />

---

### **Step 51: EC2 Instance Connect – Create endpoint** 
**What you do:** Click **Create endpoint**.  
**Explanation:** AWS provisions the endpoint (can take several minutes).

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/47a9e278-aeef-4559-a5a4-6a3d35bbf7ff" />

---

### **Step 52: EC2 Instance Connect – Refresh** 
**What you do:** Refresh the page until the endpoint shows as completed.  
**Explanation:** Wait for provisioning.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/610cf84d-1546-41ae-8d11-2b76770e6a96" />

---

### **Step 53: EC2 Instance Connect – Final Connect** 
**What you do:** Click the **Connect** button at the bottom right.  
**Explanation:** Opens the terminal inside the instance.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/35533ebd-3ed3-4d0a-9ecd-20200ca3fb90" />

---

### **Step 54: Terminal input** 
**What you do:** In the terminal run:  
```bash
ping google.com          # Should work
ping <private-IP-of-finance-server>   # Initially fails
```  
**Explanation:** Internet works, but cross-VPC ping fails → troubleshooting needed.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/d0e4525d-c1b7-4082-bd3c-3d71ab35b217" />

---

### **Step 55: Troubleshooting Connectivity Issues** 
**Fix:** Go back to the Finance security group → Edit inbound rules → Change to **All traffic** from the other two VPC CIDRs.  
**Explanation:** The previous rule was too restrictive (only ICMP). Broadening to All traffic while keeping source CIDRs limited fixes it.

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/98deec14-a5ce-4785-a8c2-19dfd877ec3e" />

---

### **Step 56: Successful Troubleshoot** 
**What you see:** Ping from Developer server to Finance server now succeeds.  
**Summary (from PDF):**  
1. Created VPCs  
2. Peered the VPCs  
3. Created instances  
4. Configured security groups  
5. Added routes  
6. Tested connectivity  

**Lab Complete!** 🎉

<img width="1362" height="765" alt="image" src="https://github.com/user-attachments/assets/749f1be9-046d-405c-a2d3-fcf89119cefb" />

---
