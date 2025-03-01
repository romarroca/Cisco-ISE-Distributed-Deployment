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

![image](https://github.com/user-attachments/assets/2e75cd5e-c596-4498-a6d8-56708f3c68a0)


Reverse Lookup Zone

![image](https://github.com/user-attachments/assets/4233bb6a-1141-4537-a043-edc88c94b077)

Certificate Authority

Certificate Services is also installed on this Domain Controller as we will need this to signed our ISE-nodes Certificate

![image](https://github.com/user-attachments/assets/454f53f3-671b-4b99-826d-f6063ec7131c)

NTP Server

NTP synchronization is essential for various aspects of ISE, including Active Directory Integration and Certificate verification. Windows Server comes with NTP services enabled by default. If, however, you find the service disabled, you should manually initiate it and set the start type to Automatic. This ensures the proper functioning of ISE's synchronization requirements.

![image](https://github.com/user-attachments/assets/ec75b744-3ced-40ea-8289-e22005efa75c)

Default-Gateway Reachability
In this case, we will be using our network router as the default gateway for our ISE.

Optional Settings
•	Certificate auto-enrollment for domain users and devices – The following certificate will be used later this document when implementing EAP-TLS. This method is a more secure way of authentication as it leverages the use of Public Key Infrastructure (PKI) that uses certificates for Server and Client authentication.

![image](https://github.com/user-attachments/assets/7214e4dc-e3a4-4e40-9bed-a730c34b529c)

Group Policy Object to enroll Domain users and computers during group policy updates.

![image](https://github.com/user-attachments/assets/8295235d-254d-4fd2-a827-33574b7e0f20)

![image](https://github.com/user-attachments/assets/25eb2848-a4ef-4bea-ac26-1c2f721176ef)

This configuration will be used on later configurations of EAP-TLS that uses certificate for authentication.
_Note: For best practice implementation, please follow your official Microsoft guidelines_

ISE Initial Deployment
This document will focus on using cisco ISE 3.2 evaluation mode.

Turn on the VM and type setup on the initial prompt.
Work through the initial setup and make sure to input the correct values.

![image](https://github.com/user-attachments/assets/2d7859b0-0385-4aef-844e-a5dc07886021)












