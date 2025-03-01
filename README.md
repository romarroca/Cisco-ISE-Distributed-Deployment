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

![image](https://github.com/user-attachments/assets/000a1a56-d573-452b-a5e3-ba46a984ada4)

Work through the initial setup and make sure to input the correct values based on your environment.

![image](https://github.com/user-attachments/assets/43f5abba-660e-48f1-ad8e-cbca1f262290)

The installation will take several minutes. After installation you will be prompted to login the cli.
Verify DNS reachability, NTP settings and application status of ISE.

![image](https://github.com/user-attachments/assets/26d8f3b5-6871-478b-b333-ea44d297c9ea)

![image](https://github.com/user-attachments/assets/41f3608a-1d7d-47ad-a6c8-f922d1d2df77)

Verify Application server is running.

![image](https://github.com/user-attachments/assets/ed9d3d61-61d2-47c5-9f7a-33e5e20579e2)

ISE node is successfully installed.
Login to gui https://ise1.lab.local or https://192.168.8.6 and make sure to upload the latest patch base on the version you are currently running. In this case, we are using ISE 3.2 and will have to push ISE patch 3. Navigate to System>Maintenance>Patch Management Install Patch.
The patch will take several minutes as it will have to upload the patch, install, and reboot the application.

![image](https://github.com/user-attachments/assets/b7e087f3-caae-4bdb-9146-1d841d560fae)

Verify successful patch installation.
 
![image](https://github.com/user-attachments/assets/3a6efe89-44a6-491b-9626-09d1dd5d4923)





























