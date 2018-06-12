﻿---
title: 'Set the PIN lifetime for voice mail: Exchange 2013 Help'
TOCTitle: Set the PIN lifetime for voice mail
ms:assetid: d17f0bf6-0ad6-40a4-bdd5-f7098f39250d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Bb124712(v=EXCHG.150)
ms:contentKeyID: 49315529
ms.date: 12/10/2017
mtps_version: v=EXCHG.150
---

# Set the PIN lifetime for voice mail

 

_**Applies to:** Exchange Online, Exchange Server 2013, Exchange Server 2016_


You can configure the PIN lifetime for users who are enabled for Unified Messaging (UM). The PIN lifetime is the maximum time that an Outlook Voice Access PIN will be valid for UM-enabled recipients. The PIN lifetime setting is configured on a UM mailbox policy and applies to all UM-enabled users associated with the UM mailbox policy.

Several PIN-related settings can be configured on a UM mailbox policy. The PIN lifetime setting controls the time interval, in days, from the date Outlook Voice Access users last changed their PIN to the date they'll be forced to change their PIN again. The range is 0 through 999, and the default is 60 days. If you enter 0, the user's PIN won't expire. We recommend that you don’t configure this setting to 0, because by doing so you greatly reduce the security of your network.


> [!IMPORTANT]
> Unified Messaging doesn't notify users when their PIN is about to expire.



For additional tasks related to Outlook Voice Access PIN security, see [PIN security procedures](pin-security-procedures-exchange-2013-help.md).

## What do you need to know before you begin?

  - Estimated time to complete: Less than 1 minute.

  - You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM mailbox policies" entry in the [Unified Messaging permissions](unified-messaging-permissions-exchange-2013-help.md) topic.

  - Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-a-um-dial-plan-exchange-2013-help.md).

  - Before you perform these procedures, confirm that a UM mailbox policy has been created. For detailed steps, see [Create a UM mailbox policy](create-a-um-mailbox-policy-exchange-2013-help.md).

  - For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>, or <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## What do you want to do?

## Use the EAC to configure the PIN lifetime

1.  In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.

2.  In the list view, select the UM dial plan you want to change, and then click **Edit** ![Edit icon](images/JJ218640.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Edit icon").

3.  On the **UM dial plan** page, under **UM Mailbox Policies**, select the UM mailbox policy you want to change, and then click **Edit** ![Edit icon](images/JJ218640.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Edit icon").

4.  Click **PIN policies**, and next to **Enforce PIN lifetime (days)**, enter a value between 0 and 999.

5.  Click **Save**.

## Use the Shell to configure the PIN lifetime

This example sets the number of days that a PIN can be used for Outlook Voice Access users who are associated with a UM mailbox policy named `MyUMMailboxPolicy` to 30.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -PINLifetime 30

This example configures the following PIN-related settings for Outlook Voice Access users who are associated with a UM mailbox policy named `MyUMMailboxPolicy`:

  - Sets the number of logon failures before the user's PIN is reset to 3.

  - Sets the maximum number of logon attempts to 5.

  - Sets the minimum PIN length to 9 digits.

  - Sets the PIN to expire in 40 days.

<!-- end list -->

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3
    -MaxLogonAttempts 5 -MinPINLength 9 -PINLifetime 40
