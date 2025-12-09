https://www.youtube.com/watch?v=mEOax8ywrUM
- **VPC**: Isolation and control over your own private virtual network within AWS. You define the boundaries.
- **Subnets**: Organization and segmentation of your network into logical, manageable blocks of IP addresses.
- **Route Tables**: Directs traffic to the correct destination within the VPC or to external networks.
- **Internet Gateway (IGW)**: Allows resources (in public subnets) to connect to the public internet and vice-versa.
- **NAT Gateway**: Allows private resources to initiate outbound connections to the internet (e.g., for updates) while blocking inbound requests from the internet.
- **Security Groups**: A virtual firewall at the instance level that controls specific inbound and outbound traffic to a single server.
- **Network ACLs (NACLs)**: An optional, stateless firewall at the subnet level that allows or denies traffic entering or leaving an entire subnet.
- **VPC Peering**: Connects two VPCs (e.g., a Dev VPC and a Test VPC) using private IPs, as if they are one network, without using the public internet.
- **VPC Endpoint**: Provides private access to other AWS services (like storage (S3) or databases (DynamoDB)) without needing an Internet Gateway or NAT Gateway.
- **Site-to-Site VPN**: Securely connects your physical on-premises network to your AWS VPC over the public internet.
- **Direct Connect**: Provides a private, high-speed, low-latency connection that completely bypasses the public internet for consistent performance and enhanced security.
- **Transit Gateway**: Simplifies network management by acting as a central router to connect multiple VPCs and on-premises networks, preventing complex "spaghetti" of individual connections (peering or VPNs).

                                           ┌────────────────────────────┐
                                           │        On-Premises         │
                                           │  (Corporate Data Center)   │
                                           └─────────────┬──────────────┘
                                                         │
                                    ┌─────────────────────┼─────────────────────┐
                                    │ Site-to-Site VPN    │   Direct Connect    │
                                    │ (Encrypted Tunnel)  │ (Private Link)      │
                                    └─────────────┬───────┴─────────────┬───────┘
                                                  │                     │
                                              ┌───▼─────────────────────▼───┐
                                              │        Transit Gateway       │
                                              │  (Centralized Routing Hub)   │
                                              └───▲─────────────────────▲───┘
                                                  │                     │
     ┌────────────────────────────────────────────┼─────────────────────┼─────────────────────────────┐
     │                                            │                     │                             │
┌────▼─────────────────────────────────────────┐  │    ┌────────────────▼──────────────────────────┐  │
│                 VPC (10.0.0.0/16)            │  │    │                Peered VPC                 │  │
│     (Your isolated, private AWS network)     │  │    │          (e.g., Dev / Test VPC)          │  │
└────▲─────────────────────────────────────────┘  │    └────────────────▲──────────────────────────┘  │
     │                                            │                     │                             │
     └─────────────────────────── VPC Peering ────┴─────────────────────┘                             │


 Within Primary VPC:
 ┌────────────────────────────────────────────────────────────────────────────────────────────────────┐
 │                                         VPC Components                                             │
 └────────────────────────────────────────────────────────────────────────────────────────────────────┘

                                        VPC: 10.0.0.0/16
──────────────────────────────────────────────────────────────────────────────────────────────────────────

                    ┌─────────────────────────────── Internet Gateway (IGW) ─────────────────────────────┐
                    │           (Public Internet Access for Public Subnets)                               │
                    └───────────────────────────────▲────────────────────────────────────────────────────┘
                                                    │
                                     ┌──────────────┴───────────────┐
                                     │    Public Route Table         │
                                     │ 0.0.0.0/0 → IGW               │
                                     └──────────────┬───────────────┘
                                                    │
                         ┌──────────────────────────▼──────────────────────────┐
                         │                 Public Subnet (10.0.1.0/24)         │
                         │  - EC2 (Web/App Servers)                            │
                         │  - Elastic IPs                                      │
                         │  - ALBs / NLBs                                      │
                         │                                                     │
                         │ Security Group: Instance-level stateful firewall    │
                         │ NACL: Subnet-level stateless rules                 │
                         └─────────────────────────────────────────────────────┘


                    ┌────────────────────────────── NAT Gateway ─────────────────────────────────────────┐
                    │       (Outbound-only Internet Access for Private Subnets)                           │
                    └──────────────────────────────▲─────────────────────────────────────────────────────┘
                                                    │
                                     ┌──────────────┴───────────────┐
                                     │     Private Route Table       │
                                     │ 0.0.0.0/0 → NAT Gateway       │
                                     └──────────────┬───────────────┘
                                                    │
                         ┌──────────────────────────▼──────────────────────────┐
                         │                Private Subnet (10.0.2.0/24)         │
                         │  - EC2 (App / Internal Services)                    │
                         │  - RDS (Databases)                                  │
                         │  - ElastiCache                                      │
                         │                                                     │
                         │ Security Group: Tight control                       │
                         │ NACL: Optional subnet-level firewall                │
                         └─────────────────────────────────────────────────────┘


                    ┌────────────────────────────── VPC Endpoints ────────────────────────────────────────┐
                    │ S3 Gateway Endpoint (private S3 access)                                            │
                    │ DynamoDB Gateway Endpoint                                                           │
                    │ Interface Endpoints (PrivateLink to services)                                      │
                    └────────────────────────────────────────────────────────────────────────────────────┘

──────────────────────────────────────────────────────────────────────────────────────────────────────────


