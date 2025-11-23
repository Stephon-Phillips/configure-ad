# Active Directory Deployment Walkthrough

This walkthrough covers the process of deploying a new Active Directory forest, creating administrative accounts, and joining a client machine to the domain. These steps prepare a functional domain controller environment for future identity and access management labs.

<h2>Video Demonstration</h2>

- ### [YouTube: Configuring Active Directory](https://youtu.be/YN10JL2kAig)
---

## Table of Contents
- [Installing Active Directory Domain Services](#installing-active-directory-domain-services)
- [Creating a Domain Admin Account](#creating-a-domain-admin-account)
- [Joining Client one to the Domain](#joining-client-1-to-the-domain)
---

## Installing Active Directory Domain Services
<img width="80%" height="80%" alt="Screenshot (240)" src="https://github.com/user-attachments/assets/0b97248e-c932-4f33-a4b8-11363239410e" />

Begin by setting up the first domain controller and creating a new forest.

Steps:
1. Log in to **DC 1**.  
2. Install **Active Directory Domain Services (AD DS)**.  
3. Promote the server to a Domain Controller.  
4. Create a new forest with the domain name:  
   **mydomain.com**  
5. Restart DC 1 after promotion.  
6. Log back in using the domain account:  
   **mydomain.com\labuser**

This establishes the base domain and prepares the environment for additional configuration.

---

## Creating a Domain Admin Account
<img width="80%" height="80%" alt="Screenshot (241)" src="https://github.com/user-attachments/assets/b7cf8936-3bf7-4ff2-a745-b3ce175f3c74" />

Set up the organizational structure and create a privileged admin account.

Steps:
1. Open **Active Directory Users and Computers (ADUC)**.  
2. Create the following Organizational Units (OUs):  
   - **_EMPLOYEES**  
   - **_ADMINS**  
3. Create a new employee account:  
   - Name: **Jane Doe**  
   - Username: **jane_admin**  
   - Password: **Cyberlab123!**  
4. Add **jane_admin** to the **Domain Admins** group.  
5. Log out of DC 1.  
6. Log back in as:  
   **mydomain.com\jane_admin**

Use this new domain admin account for all remaining steps in the lab.

---

## Joining Client 1 to the Domain
<img width="80%" height="80%" alt="Screenshot (242)" src="https://github.com/user-attachments/assets/76e747d1-b200-4b6a-949a-ec36ff0af566" />

Connect a client computer to the newly created domain.

Steps:
1. In the Azure Portal, verify Client 1 DNS is set to the private IP of **DC 1**  
   (this step is already completed in the lab).  
2. Restart Client 1  
   (also already completed).  
3. Log in to Client 1 using the **local admin account (labuser)**.  
4. Join the client to the domain:  
   **mydomain.com**  
   (Client 1 will restart automatically).  
5. Log in to **DC 1** and open ADUC.  
6. Confirm that Client 1 appears in the computers container.  
7. Create a new Organizational Unit: **_CLIENTS**  
8. Move **Client 1** into the **_CLIENTS** OU.

