<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of  Active Directory within Azure Virtual Machines. by initiating the creation process for the Domain Controller Virtual Machine (VM) utilizing Windows Server 2022, and designate it as 'DC-1.' 

During this setup, take careful note of the Resource Group and Virtual Network (VNet) automatically generated. Subsequently, proceed to create the Client Virtual Machine (VM) running Windows 10, identified as 'Client-1.' It is imperative to utilize the identical Resource Group and Virtual Network that were established previously.
Furthermore, ensure that both VMs are situated within the same Virtual Network. You can verify the network topology using the Network Watcher tool to confirm the desired configuration.
 <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Install Active Directory
- Create an Admin and Normal User Account in AD
- Remote Desktop for non-administrative users
- Create a bunch of additional users

<h2>Deployment and Configuration Steps</h2>

![image](https://github.com/justinmccuff/configure-ad/assets/143865133/b406af22-80da-4ca0-8539-ec94511dee0f)

<p>
Initiate the login process to access the Domain Controller Virtual Machine, denoted as 'DC-1.' Subsequently, enable ICMPv4 within the local Windows Firewall settings. Return to the 'Client-1' virtual machine and verify the successful execution of the ping command.

Upon confirming the successful pings, re-access 'DC-1' and proceed to install the Active Directory Domain Services. To initiate the Active Directory installation process, navigate to the 'Start' menu and search for 'Server Manager.' Within the Server Manager interface, select 'Add Roles and Features.'

Follow the highlighted steps meticulously, ensuring that you specifically select 'Active Directory Domain Services (Install).' Complete the installation process by following the subsequent prompts.

</p>
<br />

![image](https://github.com/justinmccuff/configure-ad/assets/143865133/990fbfa3-0d9c-428d-8fbb-458dfaadefbf)

<p>
Next, access Active Directory to initiate the creation of two new Organizational Units (OUs). To achieve this, adhere to the following steps:

Right-click on the domain you established when initially configuring Active Directory.
Navigate to the 'New' option and select 'Organizational Unit (OU).'
Name the first OU '_EMPLOYEES.'
Create another OU and designate it '_ADMINS.'
Once the OUs have been successfully created, proceed to create a new user account. Follow these steps:

Within the Active Directory interface, repeat the previous steps, but this time, instead of selecting 'Organizational Unit (OU),' click on 'User.'
Generate a new user account for an employee, ensuring to record the username and password securely.
After creating the new user, log out of 'DC-1,' and then log back in using the newly established user credentials.</p>
<br />

![image](https://github.com/justinmccuff/configure-ad/assets/143865133/68b21e1c-8c60-4737-8eb5-658eb0c933c3)
![image](https://github.com/justinmccuff/configure-ad/assets/143865133/7486927a-6341-4e39-85db-0711c1976b50)


<p>
To establish remote desktop access on the 'Client-1' computer, please follow these meticulous steps:

Begin by logging into 'Client-1' using the same 'domain.com' domain and username that you created in the initial two instructions provided above.
Access the system properties by right-clicking on 'This PC' or 'My Computer,' and then select 'Properties.' This will open up the System Properties window.
Within the System Properties window, navigate to the 'Remote' tab. Here, you will find 'Remote Desktop' settings. Click on 'Remote Desktop.'
In the Remote Desktop settings, you will want to allow access for 'domain users.' This step ensures that users within your domain can utilize remote desktop functionality. Once you have enabled access for 'domain users,' you can proceed to log into 'Client-1' as a regular, non-administrative user. This allows you to access the computer remotely, facilitating efficient tasks and troubleshooting.

Now, let's move on to creating additional user accounts. While coding is an option for advanced users, for those less familiar with coding, here's an alternative method:
To create new user accounts, you can replicate the process described in the initial instructions for user creation on 'DC-1.' This involves using the Active Directory tools to add new users to your domain. Simply follow the steps outlined in 'Creating an Admin and Normal User Account in AD' to generate user accounts as needed. As an advanced option, Windows PowerShell Integrated Scripting Environment (ISE) can also be utilized for efficient bulk user creation. The example above demonstrates how multiple users can be generated using PowerShell scripting. After successfully creating 2-3 additional user accounts, you can proceed to test the newly created accounts by attempting to log in using one of them on the 'Client-1' computer.

These comprehensive steps ensure a seamless setup and user management process within your domain environment

</p>
<br />
