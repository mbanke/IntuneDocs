---
# required metadata
title: What's new in previous months in the Microsoft Intune - Azure | Microsoft Docs
titlesuffix: 
description: Review older announcements from the Intune what's new page
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c

# optional metadata

ROBOTS: NOINDEX,NOFOLLOW
#audience:
#ms.devlang:
ms.reviewer:
ms.suite: ems
#ms.tgt_pltfrm:
ms.custom: intune-azure
---

# What's new in the Microsoft Intune - previous months

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## November 2017

### Troubleshoot enrollment issues  <!-- 746324 -->

The **Troubleshoot** workspace now shows user enrollment issues. Details about the issue and suggested remediation steps can
help administrators and help desk operators troubleshoot problems. Certain enrollment issues aren't captured and some errors
might not have remediation suggestions.

### Group-assigned enrollment restrictions <!-- 747598 -->

As an Intune administrator, you can now [create custom Device Type and Device Limit enrollment restrictions for user groups](enrollment-restrictions-set.md).

The Intune Azure portal lets you create up to 25 instances of each restriction type, which can then be assigned to user groups. Group-assigned restrictions override the default restrictions.

All the instances of a restriction type are maintained in a strictly ordered list. This order defines a priority value for conflict resolution. A user impacted by more than one restriction instance is only restricted by the instance with the highest priority value. You can change a given instance's priority by dragging it to a different position in the list.

This functionality will be released with the migration of Android for Work settings from the Android For Work enrollment menu to the Enrollment Restrictions menu. Since this migration may take several days, your account may be upgraded for other parts of the November release before you see group assignment become enabled for Enrollment Restrictions.

### Support for multiple Network Device Enrollment Service (NDES) connectors <!-- 1528104 -->

NDES allows mobile devices running without domain credentials to obtain certificates based on the Simple Certificate Enrollment Protocol (SCEP).
With this update, multiple NDES connectors are supported.

### Manage Android for Work devices independently from Android devices <!-- 1490731 EEready-->

Intune supports managing enrollment of Android for Work devices independently from the Android platform. These settings are managed under **Device Enrollment** > **Enrollment restrictions** > **Device Type Restrictions**. (They were previously located under **Device Enrollment** > **Android for Work Enrollment** > **Android for Work Enrollment Settings**.)

By default, your Android for Work devices settings are the same as your settings for your Android devices. However, after you change your Android for Work settings that will no longer be the case.

If you block personal Android for Work enrollment, only corporate Android devices can enroll as Android for Work.

When working with the new settings, consider the following points:

#### If you have never previously onboarded Android for Work enrollment

The new Android for Work platform is blocked in the default Device Type Restrictions. After you onboard the feature, you can allow devices to enroll with Android for Work. To do so, change the default or create a new Device Type Restriction to supersede the default Device Type Restriction.

#### If you have onboarded Android for Work enrollment

If you’ve previously onboarded, your situation depends on the setting you chose:

| Setting | Android for Work status in default Device Type Restriction | Notes |
| --- | --- | --- |
| **Manage all devices as Android** | Blocked | All Android devices must enroll without Android for Work. |
| **Manage supported devices as Android for Work** | Allowed | All Android devices that support Android for Work must enroll with Android for Work. |
| **Manage supported devices for users only in these groups as Android for Work** | Blocked | A separate Device Type Restriction policy was created to override the default. This policy defines the groups you previously selected to allow Android for Work enrollment. Users within the selected groups will continue to be allowed to enroll their Android for Work devices. All other users are restricted from enrolling with Android for Work. |

In all cases, your intended regulation is preserved. No action is required on your part to maintain the global or per-group allowance of Android for Work in your environment.

### Google Play Protect support on Android <!-- 908720 -->

With the release of Android Oreo, Google introduces a suite of security features called Google Play Protect that allow users and
organizations to run secure apps and secure Android images. Intune now supports Google Play Protect features, including SafetyNet
remote attestation. Admins can set compliance policy requirements that require Google Play Protect to be configured and healthy.
The **SafetyNet device attestation** setting requires the device to connect with a Google service to verify that the device is
healthy and is not compromised. Admins can also set a configuration profile setting for Android for Work to require that
installed apps are verified by Google Play services. If a device is not compliant with Google Play Protect requirements, conditional access might block users from accessing corporate resources.

- Learn [How to create a device compliance policy to enable Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

### Text protocol allowed from managed Apps <!-- 1414050  -->

Apps managed by the Intune App SDK are able to send SMS messages.


### App install report updated to include Install Pending status <!-- 1249446 -->  

The **App install status** report, accessible for each app through the **App** list in the **Mobile apps** workload, now contains an **Install Pending** count for Users and Devices.

### iOS 11 app inventory API for Mobile Threat Detection <!-- 1391759 -->

Intune collects app inventory information from both personal and corporate-owned devices and makes it available for Mobile Threat Detection (MTD) providers to fetch, such as Lookout for Work. You can collect an app inventory from the users of iOS 11+ devices.

**App inventory**  
Inventories from both corporate-owned iOS 11+ and personally owned devices are sent to your MTD service provider. Data in the app inventory includes:

 - App ID
 - App Version
 - App Short Version
 - App Name
 - App Bundle Size
 - App Dynamic Size
 - App is validated or not
 - App is managed or not

### Migrate hybrid MDM users and devices to Intune standalone <!-- 1463747 wnready -->
New processes and tools are now available for moving users and their devices from hybrid MDM to Intune in the Azure portal, allowing you to do the following tasks:
- Copy policies and profiles from the Configuration Manager console to Intune in the Azure portal
- Move a subset of users to Intune in the Azure portal, while keeping the rest in hybrid MDM
- Migrate devices to Intune in the Azure portal without needing to re-enroll them

For details, see [Migrate hybrid MDM users and devices to Intune standalone](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### On-premises Exchange connector high availability support  <!-- 676614 -->
After the Exchange connector creates a connection to Exchange using the specified CAS, the connector now has the ability to discovery other CASs. If the primary CAS becomes unavailable, the connector will fail over to another CAS, if available, until the primary CAS becomes available. For details, see [On-premises Exchange connector high availability support](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### Remotely restart iOS device (supervised only) <!-- 1424595 -->

You can now trigger a supervised iOS 10.3+ device to restart using a device action. For more information on using the device restart action, see [Remotely restart devices with Intune](device-restart.md).

> [!Note]
> This command requires a supervised devices and the **Device Lock** access right. The device restarts immediately. Passcode-locked iOS devices will not rejoin a Wi-Fi network after restart; after restart, they may not be able to communicate with the server.

### Single Sign-on support for iOS <!-- 1333645 -->  

You can use Single Sign-on for iOS users. The iOS apps that are coded to look for user credentials in the Single Sign-on payload are functional with this payload configuration update. You can also use UPN and Intune Device ID to configure the Principal Name and Realm. For details, see [Configure Intune for iOS device single sign-on](sso-ios.md).

### Add "Find my iPhone" for personal devices <!--1427287-->
You can now view whether iOS devices have Activation Lock turned on. This feature previously could be found in the Intune in the classic portal.

### Remotely lock managed macOS device with Intune <!-- 1437691 -->

You can lock a lost macOS device, and set a 6-digit recovery PIN. When locked, the **Device overview** blade displays the PIN until another device action is sent.

For more information, see [Remotely lock managed devices with Intune](device-remote-lock.md).

### New SCEP profile details supported <!-- 1559808 -->

Administrators are now able to set additional settings when creating a SCEP profile on Windows, iOS, macOS, and Android platforms.  Administrators can set IMEI, serial number, or common name including email in the subject name format.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### Retain data during a factory reset  <!--1588489 -->
When resetting Windows 10 version 1709 and later to factory settings, a new capability is available. Admins can specify if device enrollment and other provisioned data are retained on a device through a factory reset.

The following data is retained through a factory reset:
- User accounts associated with the device
- Machine state (domain join, Azure Active Directory-joined)
- MDM enrollment
- OEM installed apps (store and Win32 apps)
- User profile
- User data outside of user profile
- User autologon

The following data is not retained:
- User files
- User installed apps (store and Win32 apps)
- Non-default device settings


### Window 10 update ring assignments are displayed <!-- 1621837 -->
When you are **Troubleshooting,** for the user you are viewing, you are able to see any Windows 10 update rings assignments.  

### Windows Defender Advanced Threat Protection reporting frequency settings  <!-- 1455974  -->
Windows Defender Advanced Threat Protection (WDATP) service allows admins to manage reporting frequency for managed devices. With the new **Expedite telemetry reporting frequency** option, WDATP collects data and assesses risks more frequently. The default for reporting optimizes speed and performance. Increasing the frequency of reporting can be valuable for high-risk devices. This setting can be found in the **Windows Defender ATP** profile in **Device configurations**.

### Audit updates <!-- 1412961 -->  
Intune auditing provides a record of change operations related to Intune.  All create, update, delete, and remote task operations are captured and retained for one year.  The Azure portal provides a view of the last 30 days of audit data in each workload, and is filterable.  A corresponding Graph API allows retrieval of the auditing data stored for the last year.

Auditing is found under the **MONITOR** group. There is an **Audit Logs** menu item for each workload.

### Company Portal app for macOS is available <!--1541700-->
The Intune Company Portal on macOS has an updated experience, which has been optimized to cleanly display all the information and compliance notifications your users need for all the devices they have enrolled. And, once the Intune Company Portal has been deployed to a device, Microsoft AutoUpdate for macOS will provide updates to it. You can download the new Intune Company Portal for macOS by logging into the Intune Company Portal website from a macOS device.

### Microsoft Planner is now part of the mobile app management (MAM) list of approved apps  <!-- 1248473 -->
The Microsoft Planner app for iOS and Android is now part of the approved apps for mobile app management (MAM). The app can be configured through the Intune App Protection blade in the Azure portal to all tenants.
- Learn more the [MAM list of approved apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### Per-App VPN requirement update frequency on iOS devices   <!-- 1547061 -->  
Administrators may now remove Per-App VPN requirements for apps on iOS devices; affected devices will after their next Intune check-in, which generally occurs within 15 minutes.  

### Support for System Center Operations Manager management pack for Exchange connector <!-- 885457 -->
The System Center Operations Manager (SCOM) management pack for Exchange connector is now available to help you parse the Exchange connector logs. This feature gives you different ways of monitoring the service when you need to troubleshoot issues.

### Co-management for Windows 10 devices  <!-- 1243445 -->
Co-management is a solution that provides a bridge from traditional to modern management, and it provides you with a path to make the transition using a phased approach. At its foundation, co-management is a solution where Windows 10 devices are concurrently managed by Configuration Manager and Microsoft Intune, as well as joined to Active Directory (AD) and Azure Active Directory (Azure AD).  This configuration provides you with a path to modernize over time, at the pace that’s right for your organization if you can’t move all at once.  

### Restrict Windows Enrollment by OS version <!-- 245498 -->
As an Intune administrator, you can now specify a minimum and maximum version of Windows 10 for device enrollments. You can set these restrictions in the **Platform Configurations** blade.

Intune will continue to support enrolling Windows 8.1 PCs and phones. However, only Windows 10 versions can be set with minimum and maximum limits. To permit enrollment of 8.1 devices, leave the minimum limit empty.

### Alerts for Windows AutoPilot unassigned devices  <!-- 1631236 -->
A new alert is available for Windows AutoPilot unassigned devices on the **Microsoft Intune** > **Device enrollment** > **Overview** page. This alert shows how many devices from the AutoPilot program do not have AutoPilot deployment profiles assigned. Use the information in the alert to create profiles and assign them to the unassigned devices. When you click the alert, you see a full list of Windows AutoPilot devices and detailed information about them. For more information, see [Enroll Windows devices using Windows AutoPilot deployment program](https://docs.microsoft.com/intune/enrollment-autopilot).


### Refresh button for Devices list    <!-- 1333581 -->
Because the Device list does not refresh automatically, you can use the new Refresh button to update the devices that display in the list.

### Support for Symantec Cloud Certification Authority (CA)  <!-- 1333638 -->    
Intune now supports Symantec Cloud CA, which allows the Intune Certificate Connector to issue PKCS certificates from the Symantec Cloud CA to Intune managed devices. If you're already using the Intune Certificate Connector with Microsoft Certification Authority (CA), you can use the existing Intune Certificate Connector setup to add the Symantec CA support.

### New items added to device inventory   <!--1404455 -->
The following new items are now available to the [inventory taken by enrolled devices](device-inventory.md):

- Wi-Fi MAC address
- Total storage space
- Total free space
- MEID
- Subscriber carrier

### Set access for apps by minimum Android security patch on the device<!-- 1278463 -->   
An administrator is able to define the minimum Android security patch that must be installed on the device in order to gain access to a managed application under a managed account.

> [!Note]  
> This feature only restricts security patches released by Google on Android 6.0+ devices.

### App-conditional launch support <!-- 1193313 -->
IT admins can now set a requirement through the Azure admin portal to enforce a passcode instead a numeric PIN through the mobile app management (MAM) when the application launch. If configured, the user is required to set and use a passcode when prompted before getting access to MAM-enlightened applications. A passcode is defined as a numeric PIN with at least one special character or upper/lowercase alphabet. This release of Intune will enable this feature **on iOS only**. Intune supports passcode in a similar way to numeric PIN, it sets a minimum length, allowing repeat characters and sequences. This feature requires the participation of applications (that is, WXP, Outlook, Managed Browser, Yammer) to integrate the Intune App SDK with the code for this feature in place for the passcode settings to be enforced in the targeted applications.

### App Version number for line-of-business in device install status report <!-- 1233999 -->
With this release, the Device install status report displays the app version number for the line-of-business apps for iOS and Android. You may use this information to troubleshoot your apps, or find devices that are running outdated app versions.

### Admins can now configure the Firewall settings on a device using a device configuration profile <!-- 951708 -->   
Admins can turn on firewall for devices, and also configure various protocols for domain, private, and public networks.  These firewall settings can be found in the "Endpoint protection" profile.

### Windows Defender Application Guard helps protect devices from untrusted websites, as defined by your organization <!-- 958257 -->   
Admins can define sites as "trusted" or "corporate" using a Windows Information Protection workflow or the new "Network boundary" profile under device configurations. If they are viewed with Microsoft Edge, any sites that aren't listed in on a 64-bit Windows 10 device’s trusted network boundary open instead in a browser within a Hyper-V virtual computer.

Application Guard can be found in the device configuration profiles, in the "Endpoint protection" profile. From there, admins can configure interaction between the virtualized browser and the host machine, nontrusted sites and trusted sites, and storing data generated in the virtualized browser. To use Application Guard on a device, a network boundary first must be configured. It's important to define only one network boundary for a device.  

### Windows Defender Application Control on Windows 10 Enterprise provides mode to trust only authorized apps <!-- 1031096 -->    
With thousands of new malicious files created every day, using antivirus signature-based detection to fight against malware might no longer provide an adequate defense against new attacks. Using Windows Defender Application Control on Windows 10 Enterprise, you can change device configuration from a mode where apps are trusted unless blocked by an antivirus or other security solution, to a mode where the operating system trusts only apps authorized by your enterprise. You assign trust to apps in Windows Defender Application Control.

Using Intune, you can configure the application control policies either in "audit only" mode or enforce mode. Apps aren't blocked when running in “audit only” mode. “Audit only” mode logs all events in local client logs. You can also configure whether only Windows components and Microsoft Store apps are allowed to run or whether additional apps with good reputations as defined by the Intelligent Security Graph are allowed to run.

### Window Defender Exploit Guard is a new set of intrusion prevention capabilities for Windows 10 <!-- 1063615 -->   
Window Defender Exploit Guard includes custom rules to reduce the exploitability of applications, prevents macro and script threats, automatically blocks network connections to low reputation IP addresses, and can secure data from ransomware and unknown threats. Windows Defender Exploit Guard consists of the following components:

- **Attack Surface Reduction (ASR)** provides rules that allow you to prevent macro, script, and email threats.
- **Controlled Folder access** automatically blocks access to content to protected folders.
- **Network Filter** blocks outbound connection from any app to low rep IP/domain
- **Exploit Protection** provides memory, control flow, and policy restrictions that can be used to protect an application from exploits.

### Manage PowerShell scripts in Intune for Windows 10 devices <!-- 790537 -->

The Intune management extension lets you upload PowerShell scripts in Intune to run on Windows 10 devices. The extension supplements Windows 10 mobile device management (MDM) capabilities and makes it easier for you to move to modern management. For details, see [Manage PowerShell scripts in Intune for Windows 10 devices](intune-management-extension.md).

### New device restriction settings for Windows 10      <!-- 1308850 -->
-    Messaging (mobile only) - disable testing or MMS messages
-    Password - settings to enable FIPS and the use of Windows Hello devices secondary devices for authentication 
-    Display - settings to turn on or off GDI Scaling for legacy apps

### Windows 10 kiosk mode device restrictions <!-- 1308872 -->   
You can restrict Windows 10 device users to kiosk mode, which limits users to a set of predefined apps.  To do so, create a Windows 10 device restriction profile and set the Kiosk settings.

Kiosk mode supports two modes: **single app** (allows a user to run just one app) or **multi app** (permits access to a set of apps).  You define the user account and device name, which determines the supported apps).  When the user is logged in, they're limited to the defined apps.  To learn more, see [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Kiosk mode requires:

- Intune must be the MDM authority.
- The apps must already be installed on the target device.
- The device must be [properly provisioned](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### New device configuration profile for creating network boundaries <!-- 1311967 -->   
A new device configuration profile called **Network boundary** can be found with your other device configuration profiles. Use this profile to define online resources that you want to be considered corporate and trusted. You must define a network boundary for a device *before* features such as Windows Defender Application Guard and Windows Information Protection can be used on the device. It’s important to define only one network boundary for each device.

You can define enterprise cloud resources, IP address ranges, and internal proxy servers that you want to be considered trusted. Once defined, the network boundary can be consumed by other features such as Windows Defender Application Guard and Windows Information Protection.

###  Two additional settings for Windows Defender Antivirus <!-- 1338409 -->  
**File blocking level**

| | |
|---|---|
| Not Configured | **Not Configured** uses the default Windows Defender Antivirus blocking level and provides strong detection without increasing the risk of detecting legitimate files. |
| High | **High** applies a strong level of detection.
| High +  | **High +** provides the High level with additional protection measures that might impact client performance.
| Zero tolerance  | **Zero tolerance** blocks all unknown executables. |

While unlikely, setting to **High** may cause some legitimate files to be detected.
We recommend you set File blocking level to the default, **Not configured**.

**Time out extension for file scanning by the cloud**  

| | |
|--|--|
| Number of seconds (0-50) | Specify the maximum amount of time that Windows Defender Antivirus should block a file while waiting for a result from the cloud. The default amount is 10 seconds: any additional time specified here (up to 50 seconds) is added to those 10 seconds. In most cases, the scan takes much less time than the maximum. Extending the time allows the cloud to thoroughly investigate suspicious files. We recommend that you enable this setting and specify at least 20 additional seconds. |

### Citrix VPN added for Windows 10 devices <!-- 1512457 -->  
You can configure Citrix VPN for their Windows 10 devices. You can choose the Citrix VPN in the *Select a connection type* list in the **Base VPN** blade when configuring a VPN for Windows 10 and later.

> [!Note]
> Citrix configuration existed for iOS and Android.

### Wi-Fi connections support pre-shared keys on iOS <!-- 1550823 -->
Customers can configure Wi-Fi profiles to use pre-shared keys (PSK) for WPA/WPA2 Personal connections on iOS devices. These profiles are pushed to user's device when the device is enrolled into Intune.

When the profile has been pushed to the device, the next step depends on the profile configuration.  If set to connect automatically, it does so when the network is next needed.  When the profile is connects manually, the user must activate the connection manually.  

### Access to managed app logs for iOS <!-- 1469920 -->
End users with the managed Browser installed can now view the management status of all Microsoft published apps and send logs for troubleshooting their managed iOS apps.

Learn how to enable the troubleshooting mode in the Managed Browser on an iOS device, see [How to access to managed app logs using the Managed Browser on iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### Improvements to device setup workflow in the Company Portal for iOS in version 2.9.0 <!-- 1417174 -->

The device setup workflow has been improved in the Company Portal app for iOS. The language is more user-friendly and we've combined screens where possible. The language is more specific to your company by using your company name throughout the setup text. You can see this updated workflow on the [what's new in app UI page](whats-new-app-ui.md).


### User entity contains latest user data in Data Warehouse data model <!-- 1544273 -->
The first version of the Intune Data Warehouse data model only contained recent, historical Intune data. Report makers could not capture the current state of a user. In this update, the **User entity** is populated with the latest user data.


## October 2017

### iOS and Android line-of-business app version number is visible <!-- 1380712 -->

Apps in Intune now display the version number for iOS and Android line-of-business apps. The number displays in the Azure portal in the app list and in the app overview blade. End users can see the app number in the Company Portal app and in the web portal.

__Full version number__
The full version number identifies a specific release of the app. The number appears as _Version_(_Build_). For example, 2.2(2.2.17560800)

The full version number has two components:

 - **Version**  
   The version number is the human-readable release number of the app. This is used by end users to identify different releases of the app.

 - **Build Number**  
    The build number is an internal number that can be used in app detection and to programmatically manage the app. The build number refers to an iteration of the app that references changes in the code.

Learn more about version numbers and developing line-of-business apps in [Get started with the Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers).

### Device and app management integration <!-- 677972 -->   
Now that Intune’s mobile device management (MDM) and mobile application management (MAM) are both accessible from the Azure portal, Intune started integrating the IT admin experience around application and device management. These changes are geared to simplify your device and app management experience.

Learn more about the MDM and MAM changes announced in the [Intune support team blog](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### New enrollment alerts for Apple devices <!-- 1471790 -->
The overview page for enrollment will show useful alerts for IT admins regarding management of Apple devices. Alerts will show up on Overview page when the Apple MDM push certificate is expiring or has already expired; when the Device Enrollment Program token is expiring or has already expired; and when there are unassigned devices in the Device Enrollment Program.

### Support token replacement for app configuration without device enrollment <!-- 1080364 -->

You can use tokens for dynamic values in app configurations for apps on devices that are not enrolled. For more information, see [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md).

### Updates to the Company Portal app for Windows 10 <!--1299474-->
The Settings page in the Company Portal app for Windows 10 has been updated to make the settings and intended user actions to be more consistent across all settings. It has also been updated to match the layout of other Windows apps. You can find before/after images in the [what's new in app UI](whats-new-app-ui.md) page.

### Inform end users what device information can be seen for Windows 10 devices <!--1337920-->
We have added **Ownership Type** to the Device Details screen on the Company Portal app for Windows 10. This will allow users to find out more about privacy directly from this page from the Intune end user docs. They will also be able to locate this information on the **About** screen.

### Feedback prompts for the Company Portal app for Android <!--1165249-->
The Company Portal app for Android now requests end user feedback. This feedback is sent directly to Microsoft, and provides end users with an opportunity to review the app in the public Google Play store. Feedback is not required, and can easily be dismissed so users can continue using the app.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### Helping your users help themselves with the Company Portal app for Android <!-- 1573324, 1573150, 1558616, 1564878 -->

The Company Portal app for Android has added instruction for end users to help them understand and, where possible, self-solve on new use cases.
- End users will be guided to the [Azure Active Directory portal](https://account.activedirectory.windowsazure.com/r/#/profile) to remove a device if they have reached the maximum number of devices that they are allowed to add.
- End users are given steps to follow to help them [fix activation errors on Samsung Knox devices](https://go.microsoft.com/fwlink/?linkid=859718) or to [turn off power-saving mode](/intune-user-help/power-saving-mode-android). If neither of those solutions resolve their issue, we will provide an explanation of how to [submit logs to Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### New 'Resolve' action available for Android devices <!-- 1583480 -->

The Company Portal app for Android is introducing a 'Resolve' action on the _Update device settings_ page. Selecting this option will take the end user directly to the setting that is causing their device to be noncompliant. The Company Portal app for Android currently supports this action for the [device passcode](/intune-user-help/set-your-pin-or-password-android), [USB debugging](/intune-user-help/you-need-to-turn-off-usb-debugging-android), and [Unknown Sources](/intune-user-help/you-need-to-turn-off-unknown-sources-android) settings.

### Device setup progress indicator in Android Company Portal <!-- 1565657 -->
The Company Portal app for Android shows a device setup progress indicator when a user is enrolling their device. The indicator shows new statuses, beginning with "Setting up your device...", then "Registering your device...", then "Finishing registering your device...", then "Finishing setting up your device...".

### Certificate-based authentication support on the Company Portal for iOS <!--1029830-->
We have added support for certificate-based authentication (CBA) in the Company Portal app for iOS. Users with CBA enter their username, then tap the “Sign in with a certificate” link. CBA is already supported on the Company Portal apps for Android and Windows. You can learn more on the [sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) page.

### Apps that are available with or without enrollment can now be installed without being prompted for enrollment. <!-- 1334712 -->

Company apps that have been made available with or without enrollment on the Android Company Portal app can now be installed without a prompt to enroll.

### Windows AutoPilot Deployment Program support in Microsoft Intune  <!-- 747617  -->
You can now use Microsoft Intune with Windows AutoPilot Deployment Program to empower your users to provision their corporate devices without involving IT. You can customize the out-of-box experience (OOBE) and guide users to join their device to Azure AD and enroll in Intune. Working together, Microsoft Intune and Windows AutoPilot eliminate the need to deploy, maintain, and manage operating system images. For details, see [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot).

### Quick start for device enrollment  <!-- 1425655 --> 
Quick start is now available in **Device enrollment** and provides a table of references for managing platforms and configuring the enrollment process. A brief description of each item and links to documentation with step-by-step instructions provides useful documentation to simplify getting started.

### Device categorization <!-- 1427491 -->
The enrolled devices platform chart of the **Devices > Overview** blade organizes devices by platform, including Android, iOS, macOS, Windows, and Windows Mobile.  Devices running other operating systems are grouped into "Other."  This includes devices manufactured by Blackberry, NOKIA, and others.  

To learn which devices are affected in your tenant, choose **Manage > All devices** and then use **Filter** to limit the **OS** field.

### Zimperium - New Mobile Threat Defense partner   <!-- 954681 -->  
You can control mobile device access to corporate resources using conditional access based on risk assessment conducted by Zimperium, a Mobile Threat Defense solution that integrates with Microsoft Intune.

#### How integration with Intune works
Risk is assessed based on telemetry collected from devices running Zimperium. You can configure EMS conditional access policies based on Zimperium risk assessment enabled through Intune device compliance policies, which you can use to allow or block non-compliant devices to access corporate resources based on detected threats.

### New settings for Windows 10 device restriction profile  <!--- 978575, 1308849, -->  
We are adding new settings to the Windows 10 device restriction profile in the Windows Defender SmartScreen category.

For details about the Windows 10 device restriction profile, see [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md).

### Remote support for Windows and Windows Mobile devices   <!-- 1070473 -->  
Intune can now use the [TeamViewer](https://www.teamviewer.com) software, purchased separately, to enable you to give remote assistance to your users who are running Windows, and Windows Mobile devices.

### Scan devices with Windows Defender <!-- 1280988  1280990   -->
You can now run a **Quick scan**, **Full scan**, and **Update signatures** with Windows Defender Antivirus on managed Windows 10 devices. From the device's overview blade, choose the action to run on the device. You are prompted to confirm the action before the command is sent to the device. 

**Quick scan**: A quick scan scans locations where malware registers to start, such as registry keys and known Windows startup folders. A quick scan takes an average of five minutes. Combined with the **Always-on real-time protection** setting that scans files when they are opened, closed, and whenever a user navigates to a folder, a quick scan helps provide protection from malware that might be in the system or the kernel. Users see the scan results on their devices when it finishes. 

**Full scan**: A full scan can be useful on devices that have encountered a malware threat to identify if there are any inactive components that require a more thorough clean-up, and is useful for running on-demand scans. Full scan can take an hour to run. Users see the scan results on their devices when it finishes. 

**Update signatures**: The update signature command updates Windows Defender Antivirus malware definitions and signatures. This helps ensure Windows Defender Antivirus is effective in detecting malware. This feature is for Windows 10 devices only, pending device internet connectivity. 

### The Enable/Disable button is removed from the Intune Certificate Authority page of the Intune Azure portal  <!-- 1400455 -->
 We are eliminating an extra step in setting up the certificate connector on Intune. Currently, you download the certificate connector and then enable it in the Intune console. However, if you disable the connector in the Intune console, the connector continues to issue certificates.

#### How does this affect me?
Starting in October, the Enable/Disable button will no longer appear on the Certificate Authority page in the Azure portal. Connector functionality remains the same. Certificates are still deployed to devices enrolled in Intune. You can continue to download and install the certificate connector. To stop certificates from being issued, you now uninstall the certificate connector rather than disable it.

#### What do I need to do to prepare for this change?
If you currently have the certificate connector disabled, you should uninstall it.

### New settings for Windows 10 Team device restriction profile   <!--- 1308838 -->
In this release, we’ve added many new settings to the Windows 10 Team device restriction profile to help you control Surface Hub devices.

For more information about this profile, see [Windows 10 Team device restriction settings](device-restrictions-windows-10-teams.md).

### Prevent users of Android devices from changing their device date and time  <!-- 1333292 -->
You can use an [Android custom device policy](custom-settings-android.md) to prevent Android device users from changing the device date and time.

To do this, configure an Android custom policy with the setting URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange
Set this to **TRUE**, and then assign it to the required groups.

### BitLocker device configuration <!-- 1397398 -->
The **Windows Encryption > Base Settings** include a new **Warning for another disk encryption** setting that lets you disable the [warning prompt](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) for other disk encryption that might be in use on the user's device.  The warning prompt requires end user consent before setting up BitLocker on the device and blocks BitLocker setup until confirmed by the end user.  The new setting disables the end user warning.


### Volume Purchase Program for Business apps will now sync to your Intune Tenant <!-- 800882 -->  
Third-party developers can privately distribute apps to authorized Volume Purchase Program (VPP) for Business members specified in iTunes Connect. These VPP for Business members can sign in to the Volume Purchase Program App Store and purchase their apps.

With this release, the VPP for Business apps purchased by the end user will now start syncing to their Intune tenants.

### Select Apple country store to sync VPP apps  <!-- 1332311 -->  
You can configure the Volume Purchase Program (VPP) country store when uploading your VPP token. Intune synchronizes VPP apps for all locales from the specified VPP country store.

> [!NOTE]  
> Today, Intune only synchronizes VPP apps from the VPP country store that match the Intune locale in which the Intune tenant was created.


### Block copy and paste between work and personal profiles in Android for Work <!-- 1098994 -->
With this release, you are able to configure the work profile for  Android for Work to block copy and paste between work and personal apps. You can find this new setting in the **Device restrictions** profile for the **Android for Work** Platform in **Work profile settings**.

### Create iOS apps limited to specific regional Apple App Stores <!-- 1281692 -->
You will be able to specify the country locale during the creation of an Apple App Store managed app.

> [!Note]  
> Currently, you can only create Apple App Store managed apps that are present in the US country store.

###  Update iOS VPP user and device licensed apps  <!-- 1305564 -->  
You will be able to configure the iOS VPP token to update all apps purchased for that token through the Intune service. Intune
will detect the VPP app updates inside the app store and automatically push them to the device when the device checks-in.

For steps to set a VPP token and enable automatic updates, see [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune]
(/intune/vpp-apps-ios).


### User device association entity Collection added to Intune Data Warehouse data model <!-- 1187917 -->
You can now build reports and data visualizations using the user device association information that associates user and device entity collections. The data model can be accessed through the Power BI file (PBIX) retrieved from the Data Warehouse Intune page, through the OData endpoint, or by developing a custom client.

### Review policy compliance for Windows 10 update rings <!-- 1067886 -->
You will be able to review a policy report for your Windows 10 update rings from Software updates > Per update ring deployment state. The policy report includes deployment status for the update rings that you have configured. 

### New report that lists iOS devices with older iOS versions   <!-- 1352223 -->
The **Out-of-date iOS Devices** report is available from the **Software updates** workspace. In the report, you can view a list of supervised iOS devices that were targeted by an iOS update policy and have available updates. For each device, you can view a status for why the device has not been automatically updated. 

### View app protection policy assignments for troubleshooting <!--  1475003 -->
In this upcoming release, **App protection policy** option will be added to the **Assignments** drop-down list available on the troubleshooting blade. You can now select app protection policies to see app protection policies assigned to the selected users.



### Improvements to device setup workflow in Company Portal <!--1490692-->
We've improved the device setup workflow in the Company Portal app for Android. The language is more user-friendly and specific to your company, and we've combined screens where possible. You can see these on the [what's new in app UI](whats-new-app-ui.md#week-of-october-2-2017) page.

### Improved guidance around the request for access to contacts on Android devices <!--1484985-->

The Company Portal app for Android often requires the end user to accept the Contacts permission. If an end user declines this access, they will now see an in-app notification that alerts them to grant it for conditional access. 

### Secure startup remediation for Android <!--1490712-->

End users with Android devices will be able to tap the non-compliance reason in the Company Portal app. When possible, this will take them directly to the correct location in the settings app to fix the issue. 

### Additional push notifications for end users on the Company Portal app for Android Oreo <!--1475932-->

End users will see additional notifications to indicate to them when the Company Portal app for Android Oreo is performing background tasks, such as retrieving policies from the Intune service. This increases transparency for end users about when the Company Portal is performing administrative tasks on their device. This is part of the overall [optimization of the Company Portal UI](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) for the Company Portal app for Android Oreo. 

There are further optimizations for new UI elements that are enabled in Android Oreo.  End users will see additional notifications that will indicate to them when Company Portal is performing background tasks such as retrieving policy from the Intune service.  This increases transparency for end users about when Company Portal is performing administrative tasks on the device.

### New behaviors for the Company Portal app for Android with work profiles <!-- 1485783 -->

When you enroll an Android for Work device with a work profile, it's the Company Portal app in the work profile that performs management tasks on the device. 

Unless you are using a MAM-enabled app in the personal profile, the Company Portal app for Android no longer serves any use. To improve the work profile experience, Intune will automatically hide the personal Company Portal app after a successful work profile enrollment.

The Company Portal app for Android can be enabled at any time in the personal profile by browsing for [Company Portal in the Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) and tapping **Enable**.

### Company Portal for Windows 8.1 and Windows Phone 8.1 moving to sustaining mode <!--1428681-->

Beginning in October 2017, the Company Portal apps for Windows 8.1 and Windows Phone 8.1 will move to sustaining mode. This means that the apps and existing scenarios, such as enrollment and compliance, will continue to be supported for these platforms. These apps will continue to be available for download through existing release channels, such as the Microsoft Store. 

Once in sustaining mode, these apps will only receive critical security updates. There will be no additional updates or features released for these apps. For new features, we recommend that you update devices to Windows 10 or Windows 10 Mobile. 


### Block unsupported Samsung Knox device enrollment  <!-- 1490695 -->

The Company Portal app only attempts to enroll supported Samsung Knox devices. To avoid Knox activation errors that prevent MDM enrollment, device enrollment is only attempted if the device appears in the [list of devices published by Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Samsung devices can have model numbers that support Knox while others that don't. Verify Knox compatibility with your device reseller before purchase and deployment. You can find the full list of verified devices in the [Android and Samsung Knox Standard policy settings](/intune/supported-devices-browsers.md#intune-supported-web-browsers).

### End of support for Android 4.3 and lower <!-- 1171126, 1326920 -->
Managed apps and the Company Portal app for Android will require Android 4.4 and higher to access company resources. By December, all enrolled devices will be force-retired in December, resulting in loss of access to company resources. If you are using app protection policies without MDM, apps will not receive updates, and the quality of their experience will diminish over time.

### Inform end users what device information can be seen on enrolled devices <!--1165314-->
We are adding **Ownership Type** to the Device Details screen on all Company Portal apps. This will allow users to find out more about privacy directly from the [What information can your company see?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) article. This will be rolling out across all Company Portal apps in the near future. We announced this for iOS in [September](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).

## September 2017

### Intune supports iOS 11 <!--1428975-->
Intune supports iOS 11. This was previously announced on the [Intune Support blog](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### End of support for iOS 8.0 <!-- 1164477 -->
Managed apps and the Company Portal app for iOS will require iOS 9.0 and higher to access company resources. Devices that aren't updated before this September will no longer be able to access the Company Portal or those apps. 

### Refresh action added to the Company Portal app for Windows 10 <!--1132468-->
The Company Portal app for Windows 10 allows users to refresh the data in the app by either pulling to refresh or, on desktops, pressing F5.

### Inform end users what device information can be seen for iOS <!--739894-->

We have added  **Ownership Type** to the Device Details screen on the Company Portal app for iOS. This will allow users to find out more about privacy directly from this page from the Intune end user docs. They will also be able to locate this information on the About screen.

### Allow end users to access the Company Portal app for Android without enrollment <!---1169910--->

End users will soon not have to enroll their device to access the Company Portal app for Android. End users at organizations that are using App Protection Policies will no longer receive prompts to enroll their device when they open the Company Portal app. End users will also be able to install apps from the Company Portal without enrolling the device. 


### Easier-to-understand phrasing for the Company Portal app for Android <!---1396349--->  

The enrollment process for the Company Portal app for Android has been simplified with new text to make it easier for end users to enroll. If you have custom enrollment documentation, you will want to update it to reflect the new screens. You can find sample images on our [UI updates for Intune end user apps](whats-new-app-ui.md#week-of-september-11-2017) page.

### Windows 10 Company Portal app added to Windows Information Protection allow policy <!-- 677129 -->

The Windows 10 Company Portal app has been updated to support Windows Information Protection (WIP). The app can be added to the WIP allow policy. With this change, the app no longer has to be added to the **Exempt** list.


## August 2017

### Improvements to device overview <!-- 1404453 -->  
Improvements to the device overview now display enrolled devices but excludes devices managed by Exchange ActiveSync. Exchange ActiveSync devices do not have the same management options as enrolled devices. To view the number of enrolled devices and number of enrolled devices by platform in Intune in the Azure portal, go **Devices** > **Overview**.

### Improvements to device inventory collected by Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
In this release, we’ve made the following improvements to the inventory information collected by devices you manage:
 
-   For Android devices, you can now add a column to device inventory that shows the latest patch level for each device. Add the **Security patch level** column to your device list to see this.
-   When you filter the device view, you can now filter devices by their enrollment date. For example, you could display only devices that were enrolled after a date you specify.
-   We’ve made improvements to the filter used by the **Last Check-in Date** item.
-   In the device list, you can now display the phone number of corporate owned devices.
Additionally, you can use the filter pane to search for devices by phone number.
 
For more details about device inventory, see [How to view Intune device inventory](device-inventory.md).

### Conditional access support for macOS devices 
<!-- 720172 -->
You can now set a conditional access policy that requires Mac devices to be enrolled into Intune and compliant with its device compliance policies. For example, users can download the Intune Company Portal app for macOS and enroll their Mac devices into Intune. Intune evaluate whether the Mac device is compliant or not with requirements like PIN, encryption, OS version, and System Integrity.

- Learn more about [conditional access support for macOS devices](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### Company Portal app for macOS is in public preview <!---1484796--->
The Company Portal app for macOS is now available as part of the public preview for conditional access in Enterprise Mobility + Security. This release supports macOS 10.11 and above. Get it at [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### New device restriction settings for Windows 10    
<!--1063965, 1308850  -->
In this release, we’ve added new settings for the [Windows 10 device restriction profile](/intune/device-restrictions-windows-10) in the following categories:

-   Windows Defender SmartScreen
-   App store

### Updates to the Windows 10 endpoint protection device profile for BitLocker settings
<!--1459533 -->    
In this release, we’ve made the following improvements to how BitLocker settings work in a Windows 10 endpoint protection device profile:
 
Under **Bitlocker OS drive settings**, for the setting **BitLocker with non-compatible TPM chip**, when you select **Block**, previously, this would cause BitLocker to actually be allowed. We have now fixed this to block BitLocker when it is selected.
Under **Bitlocker OS drive settings**, for the setting **Certificate-based data recovery agent**, you can now explicitly block the certificate-based data recovery agent. By default, however, the agent is allowed.
Under **BitLocker fixed data-drive settings**, for the setting **Data recovery agent**, you can now explicitly block the data recovery agent.
For more information, see [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md).


### New signed-in experience for Android Company Portal users and App Protection Policy users <!-- 621669 -->
End users can now browse apps, manage devices, and view IT contact information using the Android Company Portal app without enrolling their Android devices. In addition, if an end user already uses an app protected by Intune App Protection Policies and launches the Android Company Portal, the end user no longer receive a prompt to enroll the device.

### New setting in the Android Company Portal app to toggle battery optimization <!--1405990-->
The **Settings** page in the Company Portal app for Android has a new setting that easily lets users turn off battery optimization for Company Portal and Microsoft Authenticator apps. The app name shown in the setting will vary depending on which app manages the work account. We recommend that users turn battery optimization off for better performance of work apps that sync email and data. 

### Multi-identity support for OneNote for iOS      <!-- 1234281 -->
End users can now use different accounts (work and personal) with Microsoft OneNote for iOS. App protection policies can be applied to corporate data in work notebooks without affecting their personal notebooks. For example, a policy can allow a user to find information in work notebooks, but will prevent the user from copying and pasting and corporate data from the work notebook to a personal notebook.
 
- Learn more about the apps that support [app protection and multi-identity](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) with Intune.

### New settings to allow and block apps on Samsung Knox Standard devices
<!-- 1305423 822899-->  
In this release, we are adding new [device restriction settings](device-restrictions-android.md) that let you specify the following app lists:
 
- Apps that users are allowed to install
- Apps that users are blocked from running
- Apps that are hidden from the user on the device
 
You can specify the app by URL, package name or from the list of apps you manage.

### New Azure AD app-based conditional access policy UI link from Intune
<!-- 1016201 -->
IT admins can now set app-based conditional policies via the new conditional access policy UI in the Azure AD workload. The app-based conditional access that is in the Intune App Protection section in the Azure portal will remain there for the time being and will be enforced side-by-side. There’s also a convenience link to the new conditional access policy UI in the Intune workload.

- Learn more about [app-based conditional access on Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## July 2017

### Restrict Android and iOS device enrollment restriction by OS version  <!--- 1333256,  1245463 --->
Intune now supports restricting iOS and Android enrollment by operating system version number. Under **Device Type Restriction**, the IT admin can now set a platform configuration to restrict enrollment between a minimum and maximum operating system value. Android operating system versions must be specified as Major.Minor.Build.Rev, where Minor, Build and Rev are optional. iOS versions must be specified as Major.Minor.Build where Minor and Build are optional. Learn more about [device enrollment restrictions](enrollment-restrictions-set.md).

>[!NOTE]
>Does not restrict enrollment through Apple enrollment programs or Apple Configurator.

### Restrict Android, iOS, and macOS device personally owned device enrollment  <!--- 1333272,  1333275, 1245709 --->
Intune can restrict personal device enrollment by white-listing corporate device IMEI numbers. Intune has now expanded this functionality to iOS, Android, and macOS using device serial numbers. By uploading the serial numbers to Intune, you can predeclare devices as corporate-owned. Using enrollment restrictions, you can block personally owned (BYOD) devices, allowing enrollment only for corporate-owned devices. Learn more about [device enrollment restrictions](enrollment-restrictions-set.md).

To import serial numbers, go **Device enrollment** > **Corporate device identifiers** and click **Add** and then upload a .CSV file (no header, two columns for serial number and details like IMEI numbers).  To restrict personally owned devices, go **Device enrollment** > **Enrollment restrictions**. Under **Device Type Restrictions**, select the **Default** and then select **Platform Configurations**. You can **Allow** or **Block** personally owned devices for iOS, Android, and macOS. 


### New device action to force devices to sync with Intune <!-- 711369 -->
In this release, we've added a new device action that forces the selected device to immediately check in with Intune. When a device checks in, it immediately receives any pending actions or policies that have been assigned to it.  This action can help you to immediately validate and troubleshoot policies you’ve assigned, without waiting for the next scheduled check-in.
For details, see [Synchronize device](device-sync.md)

### Force supervised iOS devices to automatically install the latest available software update <!-- 777100 -->
A new policy is available from the Software updates workspace where you can force supervised iOS devices to automatically install the latest available software update. For details see, [Configure iOS update policies](/intune/software-updates-ios)

### Check Point SandBlast Mobile - New Mobile Threat Defense partner  <!-- 954651, 1172027 -->
You can control mobile device access to corporate resources using conditional access based on risk assessment conducted by Checkpoint SandBlast Mobile, a mobile threat defense solution that integrates with Microsoft Intune.

#### How integration with Intune works?
Risk is assessed based on telemetry collected from devices running Checkpoint SandBlast Mobile. You can configure EMS conditional access policies based on Checkpoint SandBlast Mobile risk assessment enabled through Intune device compliance policies. You can allow or block noncompliant devices access to corporate resources based on detected threats.


### Deploy an app as available in the Microsoft Store for Business <!-- 748101 -->
With this release, admins can now assign the Microsoft Store for Business as available. When set as available, end-users can install the app from the Company Portal app or website without being redirected to the Microsoft Store.

### UI updates to the Company Portal website <!--1313244 part 1-->
We made several updates to the UI of the [Company Portal website](https://portal.manage.microsoft.com) to enhance the end user experience.

- __Enhancements to app tiles__:  App icons will now display with an automatically generated background based on the dominant color of the icon (if it can be detected). When applicable, this background replaces the gray border that was previously visible on app tiles.

    The Company Portal website displays large icons whenever possible in an upcoming release. We recommend that IT admins publish apps using high-resolution icons with a minimum size of 120 x120 pixels. 

- __Navigation changes__: Navigation bar items are moved to the hamburger menu in the top left. The Categories page is removed. Users can now filter content by category while browsing.

- __Updates to Featured Apps__: We've added a dedicated page to the site where users can browse apps that you've chosen to feature, and made some UI tweaks to the Featured section on the homepage.

### iBooks support for the Company Portal website <!--1231841-->
We've added a dedicated page to the Company Portal website that allows users to browse and download iBooks. 


### Additional help desk troubleshooting details <!---  Applies to 1263399, 1326964, 1341642 --->
Intune has updated the troubleshooting display and added to the information that it provides for admins and help desk staff. You can now see an **Assignments** table that summarizes all assignments for the user based on group membership. This list includes:
- Mobile apps
- Compliance policies
- Configuration profiles
 
In addition, the **Devices** table now includes **Azure AD join type** and **Azure AD compliant** columns. For more information, see [help users troubleshoot problems](help-desk-operators.md).



### Intune Data Warehouse (Public Preview)
The Intune Data Warehouse samples data daily to provide a historical view of your tenant. You can access the data using a Power BI file (PBIX), an OData link that is compatible with many analytics tools, or interacting with the REST API. For more information, see [Use the Intune Data Warehouse](reports-nav-create-intune-reports.md).


### Light and dark modes available for the Company Portal app for Windows 10 <!---676547--->
End users will be able to customize the color mode for the Company Portal app for Windows 10. The user is able to make the change in the Settings section of the Company Portal app. The change will appear after the user has restarted the app. For Windows 10 version 1607 and later, the app mode will default to the system setting. For Windows 10 version 1511 and earlier, the app mode will default to the light mode.

### Enable end users to tag their device group in the Company Portal app for Windows 10 <!---807046-->
End users are now able to select which group their device belongs to by tagging it directly from within the Company Portal app for Windows 10.



## June 2017

### New role-based administration access for Intune admins   <!-- 1099990 -->  
A new conditional access admin role is being added to view, create, modify, and delete Azure AD Conditional Access policies. Previously, only global admins and security admins had this permission. Intune admins can be granted with this role permission so that they have access to conditional access policies.


### Tag corporate-owned devices with serial number <!-- 1215070 -->  
Intune now supports uploading iOS, macOS, and Android serial numbers as Corporate Device Identifiers. You can't use serial numbers to block personal devices from enrolling at this time because serial numbers are not verified during enrollment. Blocking personal devices by serial number will be released in the near future.


### New remote actions for iOS devices <!-- 854689 -->
In this release, we've added two new remote device actions for shared iPad devices that manage the Apple Classroom app:

- 	[Logout current user](device-logout-user.md) - Logs out the current user of an iOS device you choose.
- 	[Remove user](device-remove-user.md) - Deletes a user you choose from the local cache on an iOS device.


### Support for shared iPads with the iOS Classroom app <!-- 1044681 -->
In this release, we've expanded the support for managing the iOS Classroom app to include students who log into shared iPads using their managed Apple ID.


### Changes to Intune built-in apps <!-- 1332306 -->
Previously, Intune contained a number of built-in apps that you could quickly assign. Based on your feedback, we have removed this list, and you will no longer see built-in apps.
However, if you have already assigned any built-in apps, these will still be visible in the list of apps. You can continue to assign these apps as required.
In a later release, we plan to add an easier method to select and assign built-in apps from the Azure portal.

### Easier installation of Office 365 apps <!--- 1121362 --->
The new **Office 365 ProPlus** app type makes it easy for you to assign Office 365 ProPlus 2016 apps to devices that you manage which run the latest version of Windows 10. Additionally, you can also install Microsoft Project, and Microsoft Visio, if you own licenses for them. The apps you want are bundled together and appear as one app in the list of apps in the Intune console.
For more information, see [How to add Office 365 apps for Windows 10](apps-add-office365.md).


### Support for offline apps from the Microsoft Store for Business <!--- 777044 --->
Offline apps you purchased from the Microsoft Store for Business will now be synchronized to the Azure portal. You can then deploy these apps to device groups, or user groups. Offline apps are installed by Intune, and not by the store.

### Microsoft teams is now part of the App-based CA list of approved apps   <!-- 1257019 -->
The Microsoft Teams app for iOS and Android is now part of approved apps for app-based conditional access policies for Exchange and SharePoint Online. The app can be configured through the Intune App Protection blade in the Azure portal to all tenants currently using app-based conditional access.

### Managed browser and app proxy integration <!-- 1287310 -->
The Intune Managed Browser can now integrate with the Azure AD Application Proxy service to let users access internal web sites even when they are working remotely. Users of the browser simply enter the site URL as they normally would and the Managed Browser routes the request through the application proxy web gateway. For more information, see [Manage Internet access using Managed browser policies](app-configuration-managed-browser.md).

### New app configuration settings for the Intune Managed Browser <!-- 682951 -->
In this release, we've added further configurations for the Intune Managed Browser app for iOS and Android. You can now use an app configuration policy to configure the default home page and bookmarks for the browser.
For more information, see [Manage Internet access using Managed browser policies](app-configuration-managed-browser.md)

### BitLocker settings for Windows 10  <!-- 951707 -->
You can now configure BitLocker settings for Windows 10 devices using a new Intune device profile. For example, you can require that devices are encrypted, and also configure further settings that are applied when BitLocker is turned on.
For more information, see [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md).

### New settings for Windows 10 device restriction profile <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
In this release, we've added new settings for the Windows 10 device restriction profile, in the following categories:

-  Windows Defender
-  Cellular and connectivity
-  Locked screen experience
-  Privacy
-  Search
-  Windows Spotlight
-  Edge browser

For more information about Windows 10 settings, see [Windows 10 and later device restriction settings](device-restrictions-windows-10.md).


### Company Portal app for Android now has a new end user experience for App Protection Policies <!--1305217-->
Based on customer feedback, we've modified the Company Portal app for Android to show an **Access Company Content** button. The intent is to prevent end users from unnecessarily going through the enrollment process when they only need to access apps that support App Protection Policies, a feature of Intune mobile application management. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page.

### New menu action to easily remove Company Portal <!--1164569-->
Based on user feedback, the Company Portal app for Android has added a new menu action to initiate the removal of Company Portal from your device. This action removes the device from Intune management so that the app can be removed from the device by the user. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page and in the [Android end user documentation](/intune-user-help/unenroll-your-device-from-intune-android).

### Improvements to app syncing with Windows 10 Creators Update <!--676505-->
The Company Portal app for Windows 10 will now automatically initiate a sync for app install requests for devices with Windows 10 Creators Update (version 1703). This will reduce the issue of app installs stalling during the "Pending Sync" state. In addition, users will be able to manually initiate a sync from within the app. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page.

### New guided experience for Windows 10 Company Portal <!---1058938--->
The Company Portal app for Windows 10 will include a guided Intune walkthrough experience for devices that have not been identified or enrolled. The new experience provides step-by-step instructions that guide the user through registering into Azure Active Directory (required for Conditional Access features) and MDM enrollment (required for device management features). The guided experience will be accessible from the Company Portal home page. Users can continue to use the app if they do not complete registration and enrollment, but will experience limited functionality.

This update is only visible on devices running Windows 10 Anniversary Update (build 1607) or higher. You can see these changes on the [what's new in app UI](whats-new-app-ui.md) page.


### Microsoft Intune and Conditional Access admin consoles are generally available
We’re announcing the general availability of both the new Intune in the Azure portal admin console and the Conditional Access admin console. Through Intune in the Azure portal, you can now manage all Intune MAM and MDM capabilities in one consolidated admin experience, and leverage Azure AD grouping and targeting. Conditional access in Azure brings rich capabilities across Azure AD and Intune together in one unified console. And from an administrative experience, moving to the Azure platform allows you to use modern browsers.

Intune is now visible without the **preview** label in the Azure portal at portal.azure.com.

There is no action required for existing customers at this time, unless you have received one of a series of messages in the message center requesting that you take action so that we can migrate your groups. You may have also received a message center notice informing you that migration is taking longer due to bugs on our side. We are diligently continuing work to migrate any impacted customer.

### Improvements to the app tiles in the Company Portal app for iOS
We updated the design of the app tiles on the homepage to reflect the branding color you set for the Company Portal. For more information, see [what's new in app UI](whats-new-app-ui.md).

### Account picker now available for the Company Portal app for iOS
Users of iOS devices might see our new account picker when they sign into the Company Portal if they use their work or school account to sign into other Microsoft apps. For more information, see [what's new in app UI](whats-new-app-ui.md).

## May 2017

### Change your MDM authority without unenrolling managed devices <!--1103950-->
You can now change your MDM authority without having to contact Microsoft Support, and without having to unenroll and reenroll your existing managed devices. In the Configuration Manager console, you can [change your MDM authority](/sccm/mdm/deploy-use/change-mdm-authority) from Set to Configuration Manager (hybrid) to Microsoft Intune (standalone) or vice versa.


### Improved notification for Samsung Knox startup PINs <!--1087143-->
When end users need to set a start-up PIN on Samsung Knox devices to become compliant with encryption, the notification displayed to end users will bring them to the exact place in the Settings app when the notification is tapped.  Previously, the notification brought the end user to the password change screen.

### Device enrollment

#### Apple School Manager (ASM) support with shared iPad <!-- 748864, 770395-->

Intune now supports use of Apple School Manager (ASM) in place of Apple Device Enrollment Program to provide out-of-box enrollment of iOS devices. ASM onboarding is required to use the Classroom app for Shared iPads, and is required to enable syncing data from ASM to Azure Active Directory via Microsoft School Data Sync (SDS). For more information, see [Enable iOS device enrollment with Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> Configuring Shared iPads to work with the Classroom app requires iOS Education configurations in Azure are that not yet available.  This functionality will be added soon.

### Device management

#### Provide remote assistance to Android devices using TeamViewer <!-- 675418 -->

Intune can now use the [TeamViewer](https://www.teamviewer.com) software, purchased separately, to enable you to give remote assistance to your users who are running Android devices. For more information, see [Provide remote assistance for Intune managed Android devices](device-profile-android-teamviewer.md).

### App management

#### New app protection policies conditions for MAM <!-- 679864 -->

You can now set a requirement for MAM without enrollment users that enforces the following policies:

- Minimum application version
- Minimum operating system version
- Minimum Intune APP SDK version of the targeted application (iOS only)

This feature is available on both Android and iOS. Intune supports minimum version enforcement for OS platform versions, application versions, and Intune APP SDK. On iOS, applications that have the SDK integrated can also set a minimum version enforcement at the SDK level. The user will be unable to access the targeted application if the minimum requirements through the app protection policy are not met at the three different levels mentioned above. At this point, the user may either remove their account (for multi-identity applications), close the application, or update the version of the OS or application.

You can also configure additional settings to provide a non-blocking notification that recommends an OS or application upgrade. This notification can be closed and the application may be used as normal.

For more information, see [iOS app protection policy settings](app-protection-policy-settings-ios.md) and [Android app protection policy settings](app-protection-policy-settings-android.md).

#### Configure app configurations for Android for Work <!-- 621621 -->
Some Android apps from the store support managed configuration options that let an IT admin control how an app runs in the work profile. With Intune, you can now view the configurations supported by an app, and configure them from the Azure portal with a configuration designer or a JSON editor. For more information, see [Use app configurations for Android for Work](app-configuration-policies-use-android.md).

#### New app configuration capability for MAM without enrollment <!-- 677969 -->
You can now create app configuration policies through the MAM without enrollment channel. This feature is equivalent to the app configuration policies available in the mobile device management (MDM) app configuration. For an example of app configuration using MAM without enrollment, see  [Manage Internet access using Managed browser policies with Microsoft Intune](app-configuration-managed-browser.md).

#### Configure allowed and blocked URL lists for the Managed Browser <!-- 682960 -->
You can now configure a list of allowed and blocked domains and URLs for the Intune Managed Browser using app configuration settings in the Azure portal. These settings can be configured regardless of whether it is being used on a managed or unmanaged device. For more information, see [Manage Internet access using Managed browser policies with Microsoft Intune](app-configuration-managed-browser.md).

#### App protection policy helpdesk view <!-- 1069473 -->
IT Helpdesk users can now check user license status and the status of app protection policy apps assigned to users in the Troubleshooting blade. For details, see [Troubleshooting](./help-desk-operators.md).

### Device configuration

#### Control website visits on iOS devices <!-- 723832 -->
You can now control which websites users of iOS devices can visit using one of the following two methods:

- Add permitted, and blocked URLs using Apples built-in web content filter.

- Allow only specified websites to be accessed by the Safari browser. Bookmarks are created in Safari for each site you specify.

For more information, see [Web content filter settings for iOS devices](web-content-filter-settings-ios.md).

#### Preconfigure device permissions for Android for Work apps <!-- 621614 -->
For apps deployed to Android for Work device work profiles, you can now configure the permissions state for individual apps.  By default, Android apps that require device permissions such as access to location or the device camera will prompt users to accept or deny permissions.  For example, if an app uses the device's microphone, then the end user is prompted to grant the app permission to use the microphone. This feature allows you to define permissions on behalf of the end user.  You can configure permissions to a) automatically deny without notifying the user, b) automatically approve without notifying the user, or c) prompt the user to accept or deny. For more information, see [Android for Work device restriction settings in Microsoft Intune](device-restrictions-android-for-work.md).

#### Define app-specific PIN for Android for Work devices <!-- 728976, 1102534 -->
Android 7.0 and above devices with a work profile managed as an Android for Work device let the administrator define a passcode policy that only applies to apps in the work profile.  Options include:

- Define just a device-wide passcode policy - This is the passcode that the user must use to unlock their entire device.
- Define just a work profile passcode policy - Users will be prompted to enter a passcode whenever any app in the work profile is opened.
- Define both a device and work profile policy - IT admin has the choice to define both a device passcode policy and a work profile passcode policy at differing strengths (for example, a four-digit PIN to unlock the device, but a six-digit PIN to open any work app).

For more information, see [Android for Work device restriction settings in Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> This is only available on Android 7.0 and above.  By default, the end user can use the two separately defined PINs or they can elect to combine the two defined PINs into the strongest of the two.

#### New settings for Windows 10 devices <!-- 978585 -->
We've added new [Windows device restriction settings](device-restrictions-windows-10.md) that control features like wireless displays, device discovery, task switching, and SIM card error messages.

#### Updates to certificate configuration <!-- 918991 and 823198 -->
When creating a SCEP certificate profile, for <strong>Subject name format</strong>, the <strong>Custom</strong> option is available for iOS, Android, and Windows devices. Before this update, the <strong>Custom</strong> field was available for iOS devices only. For more information, see [Create a SCEP certificate profile](certificates-scep-configure.md#create-a-scep-certificate-profile).

When creating a PKCS certificate profile, for **Subject alternative name**, the **Custom Azure AD attribute** is available. The **Department** option is available when you select **Custom Azure AD attribute**. For more information, see [How to create a PKCS certificate profile](certficates-pfx-configure.md#create-a-device-configuration-profile).

#### Configure multiple apps that can run when an Android device is in kiosk mode <!-- 662059 -->
When an Android device is in kiosk mode, you could previously only configure one app that was allowed to run. You can now configure multiple apps using the app ID, store URL, or by selecting an Android app you already manage. For more information, see [Kiosk mode settings](device-restrictions-android.md#kiosk).



## April 2017

### Support for managing the Apple Classroom app
You can now manage the iOS Classroom app on iPad devices. Set up the Classroom app on the teachers iPad with the correct class and student data, then configure student iPads registered to a class, so that you can control them using the app.
For details, see [Configure iOS education settings](education-settings-configure-ios.md).

### Support for managed configuration options for Android apps <!-- 621621 -->
Android apps in the Play store that support managed configuration options can now be configured by Intune.  This feature lets IT view the list of configuration values supported by an app, and provides a guided, first-class UI to allow them to configure those values.

### New Android policy for complex PINs <!-- 722069 -->
You can now set a required [password](device-restrictions-android.md#password) type of Numeric complex in an Android device profile for devices that run Android 5.0 and above.  Use this setting to prevent device users from creating a PIN that contains repeating, or consecutive numbers, like 1111, or 1234.

### Additional support for Android for Work devices
- **Manage password and work profile settings** <!-- 612808 -->

  This new Android for Work device restriction policy now lets you manage password and work profile settings on Android for Work devices you manage.

- **Allow data sharing between work and personal profiles** <!-- 1045102 -->

This Android for Work device restriction profile now has new options to help you configure data sharing between work and personal profiles.

- **Restrict copy and paste between work and personal profiles** <!-- 1046094 -->

  A new custom device profile for Android for Work devices now lets you restrict whether copy and paste actions between work and personal apps are allowed.

For more information, see [Device restrictions for Android for Work](device-restrictions-android-for-work.md).

### Assign LOB apps to iOS and Android devices <!-- 1057568 -->
You can now assign line of business (LOB) apps for [iOS](lob-apps-ios.md) (.ipa files) and [Android](lob-apps-android.md) (.apk files) to users or devices.


###  New device policies for iOS <!-- 723774, 723815, 723826, 723830 -->
- **Apps on Home screen** - Controls which apps users see on the [Home screen of their iOS device](home-screen-settings-ios.md). This policy changes the layout of the Home screen, but does not deploy any apps.

- **Connections to AirPrint devices** - Controls which [AirPrint devices](air-print-settings-ios-macos.md) (network printers) that end users of iOS device can connect to.

- **Connections to AirPlay devices** - Controls which [AirPlay devices](airplay-settings-ios.md) (like Apple TV) that end users of iOS device can connect to.

- **Custom lock screen message** - Configures a custom message that users will see on the lock screen of their iOS device, that replaces the default lock screen message. For more information, see [Activate lost mode on iOS devices](device-lost-mode.md)

### Restrict push notifications for iOS apps <!-- 723767 -->
In an Intune device restriction profile, you can now configure the following [notification settings](app-notification-settings-ios.md) for iOS devices:

- Fully turn on or off notification for a specified app.
- Turn on or off, the notification in the notification center for a specified app.
- Specify the alert type, either **None**, **Banner**, or **Modal Alert**.
- Specify whether badges are allowed for this app.
- Specify whether notification sounds are allowed.

### Configure iOS apps to run in single app mode autonomously <!-- 737837 -->
You can now use an Intune device profile to configure iOS devices to run specified apps in [autonomous single app mode](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). When this mode is configured, and the app is run, the device is locked so that it can only run that app. An example of this is when you configure an app that lets users take a test on the device. When the app's actions are complete, or you remove this policy, the device returns to its normal state.

### Configure trusted domains for email and web browsing on iOS devices <!-- 723765 -->
From an iOS device restriction profile, you can now configure the following [domain settings](device-restrictions-ios.md#domains):

- **Unmarked email domains** - Emails that the user sends or receives which don't match the domains you specify here will be marked as untrusted.

- **Managed web domains** - Documents downloaded from the URLs you specify here will be considered managed (Safari only).  

- **Safari password auto-fill domains** - Users can save passwords in Safari only from URLs matching the patterns you specify here. To use this setting, the device must be in supervised mode and not configured for multiple users. (iOS 9.3+)


### VPP apps available in iOS Company Portal <!-- 748782 -->
You can now assign iOS volume-purchased (VPP) apps as **Available** installs to end users. End users will need an Apple Store account to install the app.

### Synchronize eBooks from Apple VPP Store <!-- 800878 -->
You can now [synchronize books](vpp-apps-ios.md) you purchased from the Apple volume-purchase program store with Intune, and assign the books to users.

### Multi-user management for Samsung Knox Standard devices <!-- 971988 -->
Devices that run Samsung Knox Standard are now supported for [multi-user management](android-enroll.md) by Intune. This means that end users can sign in and out of the device with their Azure Active Directory credentials, and the device is centrally managed whether it’s in use or not.  When end-users sign-in, they have access to apps and get any policies applied to them. When users sign out, all app data is cleared.

### Additional Windows device restriction settings <!-- 818566 -->
We've added support for additional [Windows device restriction settings](device-restrictions-windows-10.md) like additional Edge browser support, device lock screen customization, start menu customizations, Windows Spotlight search set wallpaper, and proxy setting.

### Multi-user support for Windows 10 Creators Update <!-- 822547 -->
We've added support for [multi-user management](windows-enroll.md) for devices that run the Windows 10 Creators Update and are Azure Active Directory domain-joined. This means that when different standard users log into the device with their Azure AD credentials, they will receive any apps and policies that were assigned to their user name. Users cannot currently use the Company Portal for self-service scenarios like installing apps.

### Fresh Start for Windows 10 PCs<!-- 1004830 -->
A new [Fresh Start device action](device-fresh-start.md) for Windows 10 PCs is now available.  When you issue this action, any apps that were installed on the PC are removed, and the PC is automatically updated to the latest version of Windows. This can be used to help remove pre-installed OEM apps that are often delivered with a new PC. You can configure if user data is retained when this device action is issued.

### Additional Windows 10 upgrade paths <!-- 903672 -->
You can now create an [edition upgrade policy to upgrade devices](edition-upgrade-configure-windows-10.md) to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### Bulk Enroll Windows 10 devices <!-- 747607 -->
You can now join large numbers of devices that run the Windows 10 Creators update to Azure Active Directory and Intune with Windows Configuration Designer (WCD). To enable [bulk MDM enrollment](windows-bulk-enroll.md) for your Azure AD tenant, create a provisioning package that joins devices to your Azure AD tenant using Windows Configuration Designer, and apply the package to corporate-owned devices you'd like to bulk enroll and manage. Once the package is applied to your devices, they will join Azure AD, enroll in Intune, and be ready for your Azure AD users to log on.  Azure AD users are standard users on these devices and receive assigned policies and required apps. Self-service and Company Portal scenarios are not supported currently.

### New MAM settings for PIN and managed storage locations <!-- 581122, 736644 -->
Two new app settings are now available to help you with mobile application management (MAM) scenarios:

- **Disable app PIN when device PIN is managed** - Detects if a device PIN is present on the enrolled device, and if so, bypasses the app PIN triggered by the app protection policies. This setting will allow for a reduction in the number of times a PIN prompt is displayed to users opening a MAM-enabled application on an enrolled device. This feature is available for both Android and iOS.

- **Select which storage services corporate data can be saved to** -Allows you to specify which storage locations in which to save corporate data. Users can save to the selected storage location services, which means all other storage location services not listed will be blocked.

  List of supported storage location services:

  - OneDrive
  - Business SharePoint Online
  - Local storage

### Help desk troubleshooting portal <!-- 907448 -->
The new [troubleshooting portal](help-desk-operators.md) lets help desk operators and Intune administrators view users and their devices, and perform tasks to resolve Intune technical problems.

## March 2017

### Support for iOS Lost Mode <!--431695-->
For iOS 9.3 and later devices, Intune added support for **Lost Mode**. You can now lock down a device to prevent all use and display a message and contact phone number of the device lock screen.

The end user will not be able to unlock the device until an admin disables Lost Mode. When Lost Mode is enabled, you can use the **Locate device** action to display the geographical location of the device on a map in the Intune console.

The device must be a corporate-owned iOS device, enrolled through DEP, that is in supervised mode.

For more information, see [What is Microsoft Intune device management](device-management.md)?

### Improvements to Device Actions report <!--677150-->
We’ve made improvements to the Device Actions report to improve performance. Additionally, you can now filter the report by state. For example, you could filter the report to show only device actions that were completed.”

### Custom app categories <!--748805-->
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](apps-add.md).

### Assign LOB apps to users with unenrolled devices <!--748823-->
You can now assign line-of-business apps from the store to users whether or not their devices are enrolled with Intune. If the user's device is not enrolled with Intune, they must go to the Company Portal website to install it, instead of the Company Portal app.

### New compliance reports <!--846671-->
You now have compliance reports that give you the compliance posture of devices in your company and allow you to quickly troubleshoot compliance-related issues encountered by your users. You can view information about

- Overall compliance state of devices
- Compliance state for an individual setting
- Compliance state for an individual policy

You can also use these reports to drill down into an individual device to view specific settings and policies that affect that device.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### Direct access to Apple enrollment scenarios <!--951869-->
For Intune accounts created after January 2017, Intune has enabled direct access to Apple enrollment scenarios using the Enroll Devices workload in the Azure portal. Previously, the Apple enrollment preview was only accessible from links in the Azure portal. Intune accounts created before January 2017 will require a one-time migration before these features are available in Azure. The schedule for migration has not been announced yet, but details will be made available as soon as possible. We strongly recommend creating a trial account to test out the new experience if your existing account cannot access the preview.


## February 2017

### Ability to restrict mobile device enrollment <!--747600, 795782-->
Intune is adding new enrollment restrictions that control which mobile device platforms are allowed to enroll. Intune separates mobile device platforms as iOS, macOS, Android, Windows and Windows Mobile.

* Restricting mobile device enrollment does not restrict PC client enrollment.  
* For iOS and Android only, there is one additional option to block the enrollment of personally owned devices.

Intune marks all new devices as personal unless the IT admin takes action to mark them as corporate owned, as explained in [this article](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### View all actions on managed devices <!--677150-->
A new __Device Actions__ report shows who has performed remote actions like factory reset on devices, and additionally shows the status of that action. See [What is device management?](device-management.md).

### Non-managed devices can access assigned apps <!--664691-->
As part of the design changes on the Company Portal website, iOS and Android users will be able to install apps assigned to them as "available without enrollment" on their non-managed devices. Using their Intune credentials, users will be able to log into the Company Portal website and see the list of apps assigned to them. The app packages of the "available without enrollment" apps are made available for download via the Company Portal website. Apps which require enrollment for installation are not affected by this change, as users will be prompted to enroll their device if they wish to install those apps.

### Custom app categories <!--748805-->
You can now create, edit, and assign categories for apps you add to Intune. Currently, categories can only be specified in English.
See [How to add an app to Intune](apps-add.md).

### Display device categories <!--814654-->
You can now view the device category as a column in the device list. You can also edit the category from the properties section of the device properties blade. See [How to add an app to Intune](apps-add.md).

### Configure Windows Update for Business settings <!--776716-->

Windows as a Service is the new way of providing updates for Windows 10. Starting with Windows 10, any new Feature Updates and Quality Updates will contain the contents of all previous updates. This means that as long as you've installed the latest update, you know that your Windows 10 devices are completely up-to-date. Unlike with previous versions of Windows, you now must install the entire update instead of part of an update.

By using Windows Update for Business, you can simplify the update management experience so that you don’t need to approve individual updates for groups of devices. You can still manage risk in your environments by configuring an update rollout strategy and Windows Update will make sure that updates are installed at right time. Microsoft Intune provides the ability to configure update settings on devices and gives you the ability to defer update installation. Intune doesn’t store the updates, but only the update policy assignment. Devices access Windows Update directly for the updates.Use Intune to configure and manage **Windows 10 update rings**. An update ring contains a group of settings that configure when and how Windows 10 updates get installed. For details, see [Configure Windows Update for Business settings](windows-update-for-business-configure.md).
