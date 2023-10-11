# disasterCAD_Phase 2

Project name:

3118-Disaster Recovery with IBM Cloud Virtual Servers

 

INNOVATION :

        IBM cloud is a packaged software offering which is used to setup a private cloud on the IaaS of the users choosing. Here we focus on a Disaster Recovery use case where ICP is used to setup a Kubernetes based Private cloud on VMWare as described in ICP backup.

 

    

The Disaster Recovery site is being simulated using another VMware vCenter Server on IBM Cloud (VCS) with similar hardware. VMware Site Recovery Manager (SRM) is used to manage the Disaster Recovery of the VMs. SRM is expected to recover:  • Network  • VMs used as Nodes of the cluster  • Storage Volumes 

• In addition to recovery of the VMs, the following Kubernetes state may need to be recovered if the distributed state gets corrupted. Therefore it is a good practice to backup this state and restore it in the recovered VMs if needed. The backup and restore process is described in ICP Component Backup • etcd DB

 • Image Registry • Cloudant DB  • MariaDB

 

 

High availability disaster recovery concepts 

The following concepts are used in this chapter: 

Split-brain or split-cluster : 

A cluster split-brain can occur when a subset of nodes in a cluster cannot communicate with the remaining nodes. Although it is possible for this situation to occur within thedata center, it is far more likely to happen to a cluster across data centers due to the greater exposure of the interconnecting networks to potential risk.

 Tie breaker or third site: 

In HADR clusters, it is a best practice to use a tie breaker or a third site to prevent a split-brain situation. Although it is still important to avoid this situation for clusters within a single data center, it is far less likely because multiple communication paths connect all nodes in the cluster, which is a less common situation between sites. 

Split policy :  

When a split-brain situation occurs, each partition attempts to acquire the tie breaker by placing a lock on the tie-breaker disk or on the NFS file. The partition that holds the lock on the SCSI disk or reserves the NFS file wins, and the other loses. 

Synchronous replication : 

Writes are committed at the remote storage before an acknowledgment can be returned to the application. This delay degrades the application performance and limits thedistance between the application and the remote storage to around 80 - 120 km. 

Asynchronous replication : 

Writes are cached locally in some form of non-volatile storage and an acknowledgment is returned to the application. Later, the write is committed to the remote storage, and then the record is removed from the local cache

 

 

 

 

IBM Power Virtual Server offering:

          The IBM Power Virtual Server offering provides a secure and scalable server virtualization environment that is built on the IBM Cloud platform for on-demand provisioning. The IBM Power Virtual Servers are in IBM data centers, which are distinct from the IBM Cloud servers, with separate networks and direct-attached storage. The environment is in its own pod, and the internal networks are fenced but offer connectivity options to meet customer requirements. This infrastructure design enables IBM Power Virtual Server to maintain key enterprise software certification and support because the IBM Power Virtual Server architecture is identical to the certified on-premises infrastructure. The virtual servers, also known as logical partitions (LPARs), run on IBM Power hardware with the Power VM hypervisor.

 

 

IBM Cloud Disaster Recovery Solutions : 

 IBM Cloud offers built-in capabilities and services for business continuity, resiliency, and security. IBM Cloud Disaster Recovery Solutions are categorized into three major areas: › Management: Improve the management of infrastructure, apps, processes, and entire cloud environments. › Migration: Move existing applications and data to the cloud with a portfolio of disaster recovery (DR) focused migration tools and services. › Storage: Scale capacity without interruption and deploy globally to achieve higherapplication performance

IBM Backup as a Service :

 IBM Backup as a Service (BUaaS) from IBM offers fully managed, end-to-end data protectionand data backup in a security-rich environment. Its benefits include: › Reliable data protection that complies with government and industry regulations. › Scalability based on your business needs. › Remote management and operation. › Monitoring solutions to ensure the health of data protection.

 

IBM Resiliency Services : 

IBM offers a full range of readily deployable services, solutions, and technologies  for data protection and recovery: › Security & Resiliency Consulting Services › Disaster Recovery as a Service (DRaaS) for hybrid platform recovery › Data Protection with BUaaS › Cybersecurity and recovery › Data center services

 

IBM Resiliency Disaster Recovery as a Service : 

IBM Resiliency DRaaS offers continuous business resiliency of applications, infrastructure, data, and cloud systems with health monitoring and comprehensive DR services. Its benefits include: › A less expensive operating expenses (OpEx) based solution compared to a self-managed on-premises model › Reliable DR orchestration with automation › Risk-based approach to protect critical IT services › Data-driven service environment for testing DR, patches, and upgrades. This section provides information about a few migration solutions options

 

IBM Spectrum Protect Plus :

 IBM Spectrum Protect Plus is a modern data resilience solution that provides recovery, replication, retention, and reuse for virtual machines(VMs), databases, applications, file systems, software as a service (SaaS) workloads, and containers in hybrid cloud environment.

 

 

 

Storage : 

This section provides information about a few storage solutions options. 

Actifio GO on IBM Cloud :

Actifio GO on IBM Cloud is the next-generation, multi-cloud Copy Data Management SaaS solution that enables customers to back up enterprise workloads (VMware, Hyper-V, Physical  Servers, SAP HANA, Oracle, SQL Server, and so on) directly to IBM Cloud while being able to instantly access the backup images within their data center

IBM Cloud Backup :

 IBM Cloud Backup is a full-featured, automated, and agent-based backup and recovery system that is managed through the IBM Cloud Backup Web CC browser utility. Its benefits include:

› Implement and monitor backup policies from anywhere by using a web-based GUI. 

› You can choose an IBM data center or keep the backup outside the network.

 › Recover from more than one facility by using multi-vaulting capabilities.

 › Scheduled backup with intelligent compression of data. 

› End-to-end encryption with Deltapro Deduplication.

 › Restoration options from a previous backup or available multiple other recovery points.

IBM Cloud Object Storage : 

IBM Cloud Object Storage is a flexible, cost-effective, and scalable cloud storage for unstructured data. Its benefits include: › Less expensive because you can save costs that are related to server, power, and data center space requirements. › Streamlined storage environment for increased agility and reduced downtime. › Supports exponential data growth and built-in high-speed file transfer capabilities. › Enhanced data security with role-based policies and access permissions

 

 

 

Solutions: 

Critical applications are no longer frequently hosted on the same frame (server) or, in many cases, in the same data centre, thanks to the evolution of IT operations over the past ten years. But rather than being fueled by a thorough analysis, this development frequently occurs in more fragmented ways. A thorough analysis looks at the HADR application needs and then compares those requirements to the available solutions throughout the entire infrastructure. 

For workloads running on systems powered by IBM POWER® processors and meeting the availability needs of crucial enterprise applications, IBM has long been recognised as a leader in HADR solutions. In recent years, the portfolio has grown to now cover data centre application protection for "less critical" workloads. These are the applications that don't have as strict criteria for data loss or can tolerate a somewhat longer outage. However, IBM currently offers a variety of LPAR restart alternatives if you're searching for a less expensive and complex HADR solution (for more details, see "LPAR and virtual machine restart option. 

Taking into account that mission-critical business workloads have reportedly increased by an average of 15%–36% over the past three years, the ITIC 2020 Reliability poll2 found that 87% of respondents consider 99.99% (52.56 minutes) of unplanned per server/per annum downtime to be the minimum acceptable level of reliability for those servers and applications. Even if it is not taken into account here, the same study, which deals with the projected costs of outages.

 It is a good idea to assess what is available, what has changed, and how these options match your application availability requirements now that IBM has a more extensive portfolio of HADR solutions. 

Although HADR solutions' main goal is to avoid infrastructure failures, these tools can also be used to manage maintenance and upgrade processes. For instance, PowerHA SystemMirror on AIX comes with a solution to handle Service Packs and interim patches throughout the cluster. PowerHA System Mirror development has recently put a strong emphasis on usability, thereby dispelling the long-held (and frequently false) misconception that the software is challenging to use .Organisations typically have a variety of apps with linked (but distinct) SLAs. In order to meet your various SLAs and the various OSs that can be running in your IBM Power system, IBM has a number of solutions that can either function together or independently

CAD_Phase 2

Project name:

3118-Disaster Recovery with IBM Cloud Virtual Servers

 

INNOVATION :

        IBM cloud is a packaged software offering which is used to setup a private cloud on the IaaS of the users choosing. Here we focus on a Disaster Recovery use case where ICP is used to setup a Kubernetes based Private cloud on VMWare as described in ICP backup.

 

    

The Disaster Recovery site is being simulated using another VMware vCenter Server on IBM Cloud (VCS) with similar hardware. VMware Site Recovery Manager (SRM) is used to manage the Disaster Recovery of the VMs. SRM is expected to recover:  • Network  • VMs used as Nodes of the cluster  • Storage Volumes 

• In addition to recovery of the VMs, the following Kubernetes state may need to be recovered if the distributed state gets corrupted. Therefore it is a good practice to backup this state and restore it in the recovered VMs if needed. The backup and restore process is described in ICP Component Backup • etcd DB

 • Image Registry • Cloudant DB  • MariaDB

 

 

High availability disaster recovery concepts 

The following concepts are used in this chapter: 

Split-brain or split-cluster : 

A cluster split-brain can occur when a subset of nodes in a cluster cannot communicate with the remaining nodes. Although it is possible for this situation to occur within thedata center, it is far more likely to happen to a cluster across data centers due to the greater exposure of the interconnecting networks to potential risk.

 Tie breaker or third site: 

In HADR clusters, it is a best practice to use a tie breaker or a third site to prevent a split-brain situation. Although it is still important to avoid this situation for clusters within a single data center, it is far less likely because multiple communication paths connect all nodes in the cluster, which is a less common situation between sites. 

Split policy :  

When a split-brain situation occurs, each partition attempts to acquire the tie breaker by placing a lock on the tie-breaker disk or on the NFS file. The partition that holds the lock on the SCSI disk or reserves the NFS file wins, and the other loses. 

Synchronous replication : 

Writes are committed at the remote storage before an acknowledgment can be returned to the application. This delay degrades the application performance and limits thedistance between the application and the remote storage to around 80 - 120 km. 

Asynchronous replication : 

Writes are cached locally in some form of non-volatile storage and an acknowledgment is returned to the application. Later, the write is committed to the remote storage, and then the record is removed from the local cache

 

 

 

 

IBM Power Virtual Server offering:

          The IBM Power Virtual Server offering provides a secure and scalable server virtualization environment that is built on the IBM Cloud platform for on-demand provisioning. The IBM Power Virtual Servers are in IBM data centers, which are distinct from the IBM Cloud servers, with separate networks and direct-attached storage. The environment is in its own pod, and the internal networks are fenced but offer connectivity options to meet customer requirements. This infrastructure design enables IBM Power Virtual Server to maintain key enterprise software certification and support because the IBM Power Virtual Server architecture is identical to the certified on-premises infrastructure. The virtual servers, also known as logical partitions (LPARs), run on IBM Power hardware with the Power VM hypervisor.

 

 

IBM Cloud Disaster Recovery Solutions : 

 IBM Cloud offers built-in capabilities and services for business continuity, resiliency, and security. IBM Cloud Disaster Recovery Solutions are categorized into three major areas: › Management: Improve the management of infrastructure, apps, processes, and entire cloud environments. › Migration: Move existing applications and data to the cloud with a portfolio of disaster recovery (DR) focused migration tools and services. › Storage: Scale capacity without interruption and deploy globally to achieve higherapplication performance

IBM Backup as a Service :

 IBM Backup as a Service (BUaaS) from IBM offers fully managed, end-to-end data protectionand data backup in a security-rich environment. Its benefits include: › Reliable data protection that complies with government and industry regulations. › Scalability based on your business needs. › Remote management and operation. › Monitoring solutions to ensure the health of data protection.

 

IBM Resiliency Services : 

IBM offers a full range of readily deployable services, solutions, and technologies  for data protection and recovery: › Security & Resiliency Consulting Services › Disaster Recovery as a Service (DRaaS) for hybrid platform recovery › Data Protection with BUaaS › Cybersecurity and recovery › Data center services

 

IBM Resiliency Disaster Recovery as a Service : 

IBM Resiliency DRaaS offers continuous business resiliency of applications, infrastructure, data, and cloud systems with health monitoring and comprehensive DR services. Its benefits include: › A less expensive operating expenses (OpEx) based solution compared to a self-managed on-premises model › Reliable DR orchestration with automation › Risk-based approach to protect critical IT services › Data-driven service environment for testing DR, patches, and upgrades. This section provides information about a few migration solutions options

 

IBM Spectrum Protect Plus :

 IBM Spectrum Protect Plus is a modern data resilience solution that provides recovery, replication, retention, and reuse for virtual machines(VMs), databases, applications, file systems, software as a service (SaaS) workloads, and containers in hybrid cloud environment.

 

 

 

Storage : 

This section provides information about a few storage solutions options. 

Actifio GO on IBM Cloud :

Actifio GO on IBM Cloud is the next-generation, multi-cloud Copy Data Management SaaS solution that enables customers to back up enterprise workloads (VMware, Hyper-V, Physical  Servers, SAP HANA, Oracle, SQL Server, and so on) directly to IBM Cloud while being able to instantly access the backup images within their data center

IBM Cloud Backup :

 IBM Cloud Backup is a full-featured, automated, and agent-based backup and recovery system that is managed through the IBM Cloud Backup Web CC browser utility. Its benefits include:

› Implement and monitor backup policies from anywhere by using a web-based GUI. 

› You can choose an IBM data center or keep the backup outside the network.

 › Recover from more than one facility by using multi-vaulting capabilities.

 › Scheduled backup with intelligent compression of data. 

› End-to-end encryption with Deltapro Deduplication.

 › Restoration options from a previous backup or available multiple other recovery points.

IBM Cloud Object Storage : 

IBM Cloud Object Storage is a flexible, cost-effective, and scalable cloud storage for unstructured data. Its benefits include: › Less expensive because you can save costs that are related to server, power, and data center space requirements. › Streamlined storage environment for increased agility and reduced downtime. › Supports exponential data growth and built-in high-speed file transfer capabilities. › Enhanced data security with role-based policies and access permissions

 

 

 

Solutions: 

Critical applications are no longer frequently hosted on the same frame (server) or, in many cases, in the same data centre, thanks to the evolution of IT operations over the past ten years. But rather than being fueled by a thorough analysis, this development frequently occurs in more fragmented ways. A thorough analysis looks at the HADR application needs and then compares those requirements to the available solutions throughout the entire infrastructure. 

For workloads running on systems powered by IBM POWER® processors and meeting the availability needs of crucial enterprise applications, IBM has long been recognised as a leader in HADR solutions. In recent years, the portfolio has grown to now cover data centre application protection for "less critical" workloads. These are the applications that don't have as strict criteria for data loss or can tolerate a somewhat longer outage. However, IBM currently offers a variety of LPAR restart alternatives if you're searching for a less expensive and complex HADR solution (for more details, see "LPAR and virtual machine restart option. 

Taking into account that mission-critical business workloads have reportedly increased by an average of 15%–36% over the past three years, the ITIC 2020 Reliability poll2 found that 87% of respondents consider 99.99% (52.56 minutes) of unplanned per server/per annum downtime to be the minimum acceptable level of reliability for those servers and applications. Even if it is not taken into account here, the same study, which deals with the projected costs of outages.

 It is a good idea to assess what is available, what has changed, and how these options match your application availability requirements now that IBM has a more extensive portfolio of HADR solutions. 

Although HADR solutions' main goal is to avoid infrastructure failures, these tools can also be used to manage maintenance and upgrade processes. For instance, PowerHA SystemMirror on AIX comes with a solution to handle Service Packs and interim patches throughout the cluster. PowerHA System Mirror development has recently put a strong emphasis on usability, thereby dispelling the long-held (and frequently false) misconception that the software is challenging to use .Organisations typically have a variety of apps with linked (but distinct) SLAs. In order to meet your various SLAs and the various OSs that can be running in your IBM Power system, IBM has a number of solutions that can either function together or independently

