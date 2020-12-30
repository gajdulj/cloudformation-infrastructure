# Infrastructure as Code: Cloudformation project template

### **Objective:**

Your company is creating an Instagram clone called Udagram. 
Developers pushed the latest version of their code in a zip file located in a public S3 Bucket.
You have been tasked with deploying the application, along with the necessary supporting software 
into its matching infrastructure. This needs to be done in automated IAC fashion and discarded afterwards.

### **Requirements:**

**Servers:**
* 4 servers in 2 subnets
* Used with an autoscaling group
* 2 vCPUs and 4GB of RAM
* OS: Ubuntu 18
* 10GB of disk space

**Security Groups and roles:**
* IAM Role allowing instances to use S3 service
Servers:
    * Inbound port open for servers: HTTP Port: 80 (use it with ELB & Load Balancer Health Check)
    * Outbound port open for servers: Unrestricted access
Load Balancer:
    * Inbound: all public traffic (0.0.0.0/0) on port 80
    * Outbound: only port 80 to reach internal servers
* Application needs to be in private subnets, Load balancer in public subnet.
* One of the output exports of the CloudFormation script should be the public URL of the LoadBalancer.
* Add http:// in front of the load balancer DNS Name in the output, for convenience.

**Commands:**

To create stack:

`bash create_stack.sh TestStack infra.yml parameters.json`
`sudo bash delete_stack.sh TestStack`

**Notes:**
We use tags to know what project do our resources correspond to.
