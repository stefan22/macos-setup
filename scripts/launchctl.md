```bash
# No over-reacting
# [< Apple is far from perfect, and much less so after the introduction of their SSO platform some 3 years ago. >]
------------------------------------------------------------------------------------------------------------------

# Disabling personal Undesirables: most mobile device management related services (mdm). These are personal preferences.
# If you're having MdM problems, the best way (sometimes only way) to deal with it's by creating your own mobileConfig settings with a free provider. Setting up an Apple push certificate with Apple and pushing mobileConfig profiles yourself.

# At System and local user levels. A quarantine folder created for System agents/daemons under /Users/shared

# You don't need to have SIP disable to do: `launchctl disable for any user or system/com.apple.name`, but you do for `launchctl bootout system/com.apple.name`. Some services will be re-enabled automatically after they have been disabled at next boot and others must be re-enable manually `launchctl enable sytem/com.apple.name`
# Bootout (SIP must be disable) on the other hand will destroy them into little tiny pieces and won't ever comeback.

# A safer way to disable SIP is:  `csrutil enable --without fs`.  The regular way is by running `csrutil disable` but it also disables the fileSystem (fs), Kernel, and NVRAM

# To target and disable services that only affect a user account do `launchctl disable gui/501/com.apple.name  (501 first user/admin account, 502 second user and so on)

# Create a shell script
# Copy/paste to a file at -> /usr/local/bin/
# Rename as -> name.sh
# Set execute permissions -> sudo chmod +x /usr/local/bin/name.sh
# Remove any blocking file attributes -> xattr -cr /usr/local/bin/*
# Set an alias on .zshrc -> alias name="/usr/local/bin/name.sh"
# Run file on terminal -> name

#!/usr/bin/env bash

# disable SIP first

set "$@" com.apple.AirPlayUIAgent AirPlayXPCHelper # AirPlay
set "$@" com.apple.AirPortBaseStationAgent # AirPort Wifi
set "$@" com.apple.AppleFileServer # File Sharing
set "$@" com.apple.afpfs_checkafp com.apple.afpfs_afpLoad # AppleShare
set "$@" com.apple.appleseed.seedusaged com.apple.appleseed.fbahelperd # Apple feedback
set "$@" com.apple.AOSHeartbeat         # AOS - Find My Mac
set "$@" com.apple.AOSNotificationOSX   # AOS - Find My Mac
set "$@" com.apple.AOSPushRelay         # Find My Mac daemon
set "$@" com.apple.apsd # Apple Push Notification service daemon
set "$@" com.apple.assistant_service
set "$@" com.apple.assistantd # iOS Siri
set "$@" com.apple.awacsd # facilitate connections between devices using Back to My Mac

set "$@" com.apple.bird # iCloud backing documents daemon

set "$@" com.apple.CalendarAgent
set "$@" com.apple.CallHistorySyncHelper com.apple.CallHistoryPluginHelper # IPhone
set "$@" com.apple.captiveagent # Captive Portal hacks
# set "$@" com.apple.cloudd # iCloud sync
set "$@" com.apple.cloudfamilyrestrictionsd-mac
# set "$@" com.apple.cloudpaird
set "$@" com.apple.cloudphotosd # photo sharing agent
set "$@" com.apple.cmio.AppleCameraAssistant com.apple.cmio.AVCAssistant com.apple.cmio.IIDCVideoAssistant com.apple.cmio.VDCAssistant
set "$@" com.apple.CommCenterRootHelper com.apple.CommCenter-osx # CoreTelephony
set "$@" com.apple.commerce # Mac App Store, the iTunes Store, iBooks Store, etc
set "$@" com.apple.coreparsec.silhouette # part of Siri's backend
# set "$@" com.apple.coreservices.sharedfilelistd
set "$@" com.apple.CoreLocationAgent # manages location authorization prompts

set "$@" com.apple.diagnostics_agent # diagnostics and usage data
set "$@" com.apple.DictationIM # Dictation Input Method

set "$@" com.apple.eapolcfg_auth # A launch-on-demand daemon used to configure EAP over LAN (EAPOL)


set "$@" com.apple.familycontrols
set "$@" com.apple.findmymacmessenger com.apple.findmymac
set "$@" com.apple.iCloudStats com.apple.iCloudUserNotifications com.apple.icloud.findmydeviced com.apple.icloud.findmydeviced.findmydevice-user-agent com.apple.icloud.fmfd
set "$@" com.apple.identityservicesd # iCloud/iMessage/FaceTime background stuff.
set "$@" com.apple.idsremoteurlconnectionagent

set "$@" com.apple.GameController.gamecontrollerd
set "$@" com.apple.geodMachServiceBridge

set "$@" com.apple.ifdreader # SmartCard reader daemon
set "$@" com.apple.imagent # part of iMessage/Messages/Facetime
set "$@" com.apple.imavagent # Daemon managing local camera for FaceTime calls
set "$@" com.apple.IMLoggingAgent

set "$@" com.apple.familycircled com.apple.familycontrols.useragent com.apple.familynotificationd
set "$@" com.apple.followupd # social-network integration and notifications

set "$@" com.apple.gamed # Game Center

set "$@" com.apple.knowledge-agent # Siri's proactive knowledge functionality

set "$@" com.apple.locationd # location services daemon
set "$@" com.apple.laterscheduler

set "$@" com.apple.Maps.mapspushd com.apple.Maps.pushdaemon # GEOlocation
set "$@" com.apple.ManagedClient.cloudconfigurationd com.apple.ManagedClient.enroll com.apple.ManagedClient com.apple.ManagedClient.startup
set "$@" com.apple.msrpc.echosvc com.apple.msrpc.lsarpc com.apple.msrpc.lsarpc com.apple.msrpc.mdssvc com.apple.msrpc.netlogon com.apple.msrpc.srvsvc com.apple.msrpc.wkssvc # Microsoft RPC

set "$@" com.apple.netbiosd # Microsoft's networking service

set "$@" com.apple.parentalcontrols.check
set "$@" com.apple.parsecd # Location-Based Suggestions for Siri
set "$@" com.apple.passd # Apple Pay and Wallet operations
set "$@" com.apple.personad # The system daemon backing profile photo storage
set "$@" com.apple.photoanalysisd # faces recognition
set "$@" com.apple.photolibraryd # The macOS photo library agent

set "$@" com.apple.rcd # Remote control daemon
set "$@" com.apple.RemoteDesktop.PrivilegeProxy
set "$@" com.apple.remotemanagementd
set "$@" com.apple.remotepairtool
set "$@" com.apple.revisiond # revisiond -- storage manager for document revisions
set "$@" com.apple.RFBEventHelper # ARD
set "$@" com.apple.routined # A daemon that learns the historical location patterns of a user
set "$@" com.apple.rpmuxd # remote debugging of mobile devices
set "$@" com.apple.rtcreportingd # home sharing

set "$@" com.apple.SafariBookmarksSyncAgent # use chrome :)
set "$@" com.apple.SafeEjectGPUAgent com.apple.SafeEjectGPUStartupDaemon # safely eject an external GPU
set "$@" suggestd # daemon that processes user content in order to detect con-tacts, events, named entities, etc.
set "$@" com.apple.screensharing com.apple.screensharing.agent com.apple.screensharing.MessagesAgent com.apple.screensharing.menuextra
# set "$@" com.apple.security.keychainsyncingoveridsproxy # iCloud Keychain syncing
set "$@" com.apple.Siri.agent
set "$@" com.apple.sharingd # Sharing Daemon that enables AirDrop, Shared Computers, and Remote Disc in the Finder
set "$@" com.apple.SocialPushAgent # twitter, Facebook, etc notifitication center
set "$@" com.apple.smbd # SMB - filesharing and printing services to Windows clients
set "$@" com.apple.ssinvitationagent # ScreenSharing InvitationAgent
set "$@" com.apple.suggestd # detect contacts, events, named entities, etc.

set "$@" com.apple.symptomsd com.apple.symptomsd-diag # part of the CrashReportor framework

set "$@" com.apple.telephonyutilities.callservicesd

#set "$@" com.apple.security.cloudkeychainproxy3 com.apple.security.idskeychainsyncingproxycom.apple.security.keychain-circle-notification
set "$@" com.apple.security.FDERecoveryAgent # Full Disk Encryption Key Recovery Transmission Agent
set "$@" com.apple.smb.preferences # file sharing
set "$@" com.apple.spindump com.apple.spindump_agent
set "$@" com.apple.SubmitDiagInfo # sends diagnostic information to Apple
set "$@" com.apple.syncdefaultsd # background service to sync to iCloud
set "$@" com.apple.syncservices.SyncServer
set "$@" com.apple.syncservices.uihandler

set "$@" com.apple.telephonyutilities.callservicesd # Telephony

set "$@" com.apple.uucp # Unix-to-Unix Copy

set "$@" ntalk
set "$@" tftp # Trivial File Transfer Protocol server


while [[ $# != 0 ]]; do
    for type in LaunchAgents LaunchDaemons; do
        path="/System/Library/$type/$1.plist"
        [ -e "$path" ] && {
            sudo launchctl unload -w "$path" 2> /dev/null
            sudo mv "$path" "$path".disabled
        }
    done
    shift
done;:
















:100:

```
