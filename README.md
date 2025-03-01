# Cisco-ISE-Distributed-Deployment
Visual guide on initially deploying Cisco ISE Distributed Deployment

The intention behind this document is to function as a guiding resource for those gearing up to deploy Cisco ISE, whether they are starting from scratch, transitioning from another NAC vendor, or building their own lab environment. The document is geared towards addressing specific focal points, including ISE Distributed Deployment, the foundational setup of Active Directory, DNS, Windows PKI, and the essential deployment aspects of GPO, spanning Certificate auto-enrollment and configurations for Wired/Wireless Adapter profiles.

The content of this document is based on the utilization of the following lab components:
•	EVE-NG-PRO version 5.0.1-106-PRO
•	Cisco ISE version 3.2.0.542 Patch 3, with ADE-OS Version 3.2.0.401
•	Windows Server 2022 Standard Evaluation Version 21H2, featuring OS Build 20348.587
•	A Cisco Switch operating within the EVE-NG environment, utilizing Cisco IOS Software, Linux Software (Version 15.2)

It's important to acknowledge that this document does not aim to be an exhaustive guide but rather a visual aid that complements official documentation. A foundational understanding of concepts such as Active Directory Domain Services, Certificate Authority, and Group Policy Object is assumed. Additionally, familiarity with tasks such as Cisco Switch AAA configuration and basic Windows troubleshooting is expected. By leveraging this guide, users can enhance their existing knowledge and streamline the deployment process for Cisco ISE.

Network Topology

![image](https://github.com/user-attachments/assets/f9562cb4-6bf7-4f8b-9976-7698432846dc)


Active Directory
To ensure a smooth and effective initial installation of Cisco ISE, it is crucial to possess the following information and establish connectivity to the following components:

![image](https://github.com/user-attachments/assets/054ef2d2-9429-4414-a63e-a5c9937ce35c)

Verify that there is an existing DNS entry for each ISE nodes

DNS Record

<img width="465" alt="image" src="https://github.com/user-attachments/assets/5d88c5b0-3d7e-4868-a490-ce7e0bce055d" />

Reverse Lookup Zone

<img width="468" alt="image" src="https://github.com/user-attachments/assets/9ab2d2c9-9a82-4484-ba4d-995675168dec" />

Certificate Authority

Certificate Services is also installed on this Domain Controller as we will need this to signed our ISE-nodes Certificate

<img width="468" alt="image" src="https://github.com/user-attachments/assets/a36ae40c-9011-47be-aaf6-3937daa9c2e5" />



