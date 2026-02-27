---

copyright:
  years: 2026
lastupdated: "2026-02-27"

keywords: Federal, FedRAMP, IBM Cloud for Government, IC4G, Federal Cloud, IBM Federal Cloud

subcollection: fedramp-govt-cloud

authors:
  - name: John Easton
    url: https://linkedin.com/in/johnpeaston
  - name: "John Easton"
    url: "linkedIn profile URL"

version: 1.1

deployment-url: url

use-case: Federal government, Government

industry: Federal government, Government

compliance: FedRAMP

content-type: deployment

production: false

---

{{site.data.keyword.attribute-definition-list}}

# IBM Cloud for Government (IC4G) Rev5 Secure Configuration Guidance
{: #ic4g-rev5-secure-configuration-guidance}
{: toc-content-type="deployment"}
{: toc-industry="Federal government, Government"}
{: toc-use-case="Federal government, Government"}
{: toc-compliance="FedRAMP"}
{: toc-version="1.1"}

Comprehensive security configuration guidance for IC4G services aligned with FedRAMP Revision 5 Recommended Secure Configuration (FRR-RSC) requirements. This page contains FedRAMP specific guidance for IC4G services. This guidance is a point in time reference to how to configure IC4G services and top-level administration accounts in a secure fashion.

## About FedRAMP Rev5 RSC Requirements
{: #about-fedramp-rev5-requirements}

FedRAMP Revision 5 introduces ten new Recommended Secure Configuration (FRR-RSC) requirements that cloud service providers must address to help federal agencies secure their cloud environments. IC4G provides guidance to align with these configuration requirements.

### Administrative Account Guidance
{: #admin-account-guidance}

## IC4G Rev5 Secure Configuration Guidance - Admin Guidance
{: #ic4g-admin-guidance}

This topic discusses top-level admin guidance.

**Important Disclaimer:** This document provides IC4G recommended practices and guidance only. It doesn't constitute legal, compliance, or regulatory advice. Organizations are solely responsible for determining their compliance requirements and implementing appropriate controls. Customers should verify current service capabilities and limitations through official documentation before implementation.

## FRR-RSC-01 Top-Level Administrative Accounts Guidance
{: #frr-src-01-guidance}

Providers must create and maintain guidance that includes instructions on how to securely access, configure, operate, and decommission top-level administrative accounts that control enterprise access to the entire cloud service offering.

**Note:** This guidance should explain how top-level administrative accounts are named and referred to in the cloud service offering.

In an IC4G customer account, there are three types of user accounts: Master User, Admin User and Normal User. Once set up, these users would access and operate their accounts in the same way via VPN access and subject to the privileges assigned to them.

### 1. Account Opening & Closure
{: #frr-src-01-guidance-acct-open-close}

This section describes the creation and deletion of a customer account in IBM Cloud for Government.

#### Requesting a customer account in IC4G
{: #frr-src-01-guidance-request-acct}

An IBM Salesperson fills out a form requesting the creation of a customer account in IBM Cloud for Government (IC4G). This request is reviewed and approved by the IC4G Offering Manager to ensure that it's a valid request from a known customer and the contact details aren't suspicious.

Once approved, the request is sent to IBM's Federal Quote to Cash (Q2C) group that reviews and validates all relevant details such as contact information, Master User details, billing details, and so on are provided.

#### Creation of the Master User account
{: #frr-src-01-guidance-create-mstr-account}

The Infrastructure Management System (IMS) system generates a numerical Account ID for each new account. This id has a format like *123456*. The account name is set by the Federal Q2C team based on the information entered in the account request form. Typically, it's the name of the customer organization, such as *ABC Company*, with the flexibility to modify it to reflect more detail such as a Division Name.

#### Closing an account in IC4G
{: #frr-src-01-guidance-close-account}

If a customer wants to close their account they should first make sure that all billing items have been canceled. The customer can do this at any time during the billing period. They have the option to "schedule" the cancel of the device immediately or at the end of the billing cycle. Steps to cancel items in the customer portal: *Log in to* the customer portal and navigate to Account->Billing->Billing Items and then select All Billing Items in the drop down. The customer may cancel remaining services when they're ready for those services to be stopped.

An easy way for the customer to verify everything is canceled is to check the "Next Invoice" in the customer portal by going to Account > Billing > Invoices and clicking on **Next recurring invoice** to check if anything is listed and that the amount due is zero.

After all billing items have been effectively canceled, a ticket should be created requesting the account be closed.

### 2. Master User
{: #frr-src-01-guidance-mstr-user}

In IC4G, the top-level administrative account, who is the "Owner" of the account, is referred to as the account "Master User". There is only 1 of these per account. It's created at the same time the account is created and can't be deleted.

The Federal Q2C group sets up the account and the primary account holder (Master User of the account as specified in the request form) receives a system-generated welcome email. The Master User then resets the password for the account to become usable. 2FA and Security Questions/Answers aren't set automatically and it's highly recommended that these be set up by the Master User registering the new account.

The Master User is the Owner of the account, and implicitly has any and every possible IC4G permission. So, for example, if a new permission is added to the IC4G system in the future, only the Master User would be implicitly granted that new permission. Any other user would have to have their permission set explicitly augmented with a grant for this new permission.

IC4G users are also arranged in a hierarchy. The Master User is at the root of the hierarchy: it has no parent, and every other user in the account is a normal or Admin user under the account Master User.

The privileges of a Master User cannot be downgraded or changed. Changing a Master User on an account should be done via a Support request. The Master User can update their profile for email address and most fields (Show API Key, Remove API Key, Reset Password, View Audit Log and Edit VPN Access). The Master User can't rename their user id, but they can change the User Status to any of the following: Disabled Users, Inactive Users, Pending Users, Suspended Users, IAMid Invalid Users, VPN Only Users.

Changing the "human owner" of the Master User identity (meaning the person who knows the login password, has the 2FA device, and knows the questions/answers) requires changing the email address of the Master User, clearing the 2FA and questions/answers, and then initiating a password reset workflow (or passing knowledge of these to the new owner). The current owner, if still available, can do this. If the current owner leaves before doing this, IBM Support can assist with these operations (requiring sufficient legal proof of the validity of the request to do so).

### Normal Users
{: #frr-src-01-guidance-normal-user}

A Master User using the customer portal UI would create users with the following steps:

1. Login to the IBM Cloud for Government Portal Site
2. *click* Account
3. Select Users → User List
4. Click the Add User
5. Fill the form per user

#### Personal Information
{: #frr-src-01-guidance-personal-info}

- Status
- Username
- First Name
- Last Name
- Street Address, City, Country, ZIP code
- Time Zone
- Phone
- Alt Phone

#### Login Settings
{: #frr-src-01-guidance-login-settings}

- User editable?
- Restrict access to IP
- Your current IP
- VPN password
- Confirm password
- Minimum password life in hours
- Expire password in (days)
- Prevent use of previous passwords
- Require security questions?

Valid passwords must be between 8 and 20 characters in length, with a combination of upper-case and lower-case characters, at least one number, and at least one special character.

#### Add User
{: #frr-src-01-guidance-add-user}

Once a user has been added to the account, the Master user can assign the following portal permissions to the user:

##### Administrative
{: #frr-src-01-guidance-administrative}

- Account Billing System
- Add Brand Account
- Automated Brand Migration
- Manage Account Notes
- Manage EU Supported Account Flag (This is set to **No** for all IC4G accounts)
- Manage Users
- Physically Access a Datacenter
- Update Payment Details
- View Event Log
- Activate Partner Customer Account
- Activate Customer Account
- Edit Company Profile
- Manage Email Delivery Service
- Manage Notification Subscribers
- Physically Access a Customer's CoLo Cage
- Submit One-Time Payments (This is set to **No** for all IC4G accounts)
- View Account Summary

##### Sales
{: #frr-src-01-guidance-sales}

- Add Server
- Add / Upgrade Services
- Cancel Server
- Upgrade Server
- View Billing ACH information (This isn't applicable to IC4G)
- Add / Upgrade Cloud Instances
- Add / Upgrade Storage
- Cancel Services
- Upgrade Services
- View Reseller Order Pricing (This isn't applicable to IC4G)

##### Support
{: #frr-src-01-guidance-support}

- Add Tickets
- Search Tickets
- View Tickets
- Edit Tickets
- View all Tickets

##### Security
{: #frr-src-01-guidance-security}

- Manage Certificates (SSL)
- Manage SSH Keys
- View Certificates (SSL)
- Manage SAML Authentication
- Request Compliance Report

##### Devices
{: #frr-src-01-guidance-devices}

- Access Virtual Dedicated Hosts
- All Guest Access
- Edit Hostname / Domain
- Host IDS
- Manage Configuration Template
- Manage Device Monitoring
- Manage Public Images
- Storage Manage
- View Location Reservation
- View Virtual Server Details
- View and Edit Virtual Guest
- Add IP Addresses
- All Hardware Access
- Hardware Component Hard Drive Dirty Attribute Edit
- IPMI Remote Management
- Manage Customer Hardware
- Manage Provisioning Scripts
- OS Reloads and Rescue Kernel
- View Hardware Details
- View Virtual Dedicated Host Details
- View and Edit Dedicated Host

##### Network
{: #frr-src-01-guidance-network}

- Add Compute with Public Network Port
- Manage CDN File Transfers
- Manage Firewall Rules
- Manage Load Balancers
- Manage Network Subnet Routes
- Manage Port Control
- Manage Security Groups
- View Bandwidth Statistics
- Manage Firewalls
- Manage Network Gateways
- Manage Network VLAN Spanning
- Manage Private Endpoint Services
- VPN Administration
- View CDN Bandwidth Statistics

##### Software
{: #frr-src-01-guidance-software}

- Manage Antivirus / Spyware
- Openstack Link
- View Helm
- View QuantaStor
- View and Edit Disk Images
- View and Edit Software Component
- View Licenses
- Manage Firewall Software
- View Customer Software Password
- View Plesk
- View Urchin
- View and Edit Manage Image Template
- View cPanel
- View Software Account License

### Device Access
{: #frr-src-01-guidance-device-access}

#### API and Virtual Private Network (VPN) Access
{: #frr-src-01-guidance-api-vpn-access}

In the User List there are 2 columns with hyper links for **API Key** and **VPN Access**.

To generate an API Key for a user, the Master User clicks the **Generate** hyperlink. That generates a key and launches a *pop-up notification* that the API Key has been generated.

Click View to see the key.

To Add VPN access for a user, the Master User clicks the **None** hyperlink, and a *pop-up window* appears.

Change the VPN Type drop down menu from **None** to **SSL**

The user must already exist. The VPN password should be reinput and saved to confirm the password.

#### Master User Setup VPN Access
{: #frr-src-01-guidance-vpn-access-mstr-user}

1. Account → User List
2. Select the Action (right column)
3. Edit VPN Access
4. Change the drop down VPN Type from **None** to **SSL**
5. Click Save

The VPN Access should change to SSL in the User List

The SSL User now can connect to the VPN for the two IBM Cloud for Government data center locations:

- DAL08: https://vpn.dal08.ibmcloudforgov.com/
- WDC03: https://vpn.wdc03.ibmcloudforgov.com/
- Global: https://sslvpn.ibmcloudforgov.com/

The user can log in to either VPN endpoint to gain access to their environment.

Upon logging in, the site detects if the SSL VPN is installed, and launch or download automatically.

Install the MotionPro VPN from Array Networks. If isn't installed already, that is reflected by the lack of an icon in the Windows Taskbar. This VPN connection allows access into your private network space.

The Master User or Admin User can control attributes for other non-admin users - Show API Key, Remove API Key, Reset Password, Change User Status, View Audit Log, Edit Portal Access, Edit VPN Access, Remove User.

The Master User or Admin User can change a user's User Status to any of the following - Disabled Users, Inactive Users, Pending Users, Suspended Users, IAMid Invalid Users, VPN Only Users.

## FRR-RSC-02 Top-Level Administrative Accounts Security Settings Guidance
{: #frr-src-02-admin-accounts-guidance}

Providers must create and maintain guidance that explains security-related settings that can be operated only by top-level administrative accounts and their security implications.

### Admin User
{: #frr-src-02-guidance-admin-user}

The Master User can create administrative users within the account under them and assign most of the privileges of the Master User to them. These are otherwise normal account users but with elevated permissions and rights granted to them. There should be no security-related settings that are solely managed by the Master User.

The user with admin privileges can then control attributes for other non-admin users - Show API Key, Remove API Key, Reset Password, Change User Status, View Audit Log, Edit Portal Access, Edit VPN Access, Remove User.

A Master User can change the User Status of an Admin User to any of the following: Disabled Users, Inactive Users, Pending Users, Suspended Users, IAMid Invalid Users, VPN Only Users.
