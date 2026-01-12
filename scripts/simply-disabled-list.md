```bash

# The Simply Disabled Script
#
# How to disable Services: System and User

# List them first:
# Run `launchctl print system` or `launchctl print gui/501` or `launchtl print gui/502`
#
# Pick your favs from System and/or User list
# `launchctl disable sytem/com.apple.name` and/ or `launchctl disable gui/501/com.apple.name`
#
# Once disabled they should appear at the bottom of each list
# Run `launchctl print system` or `launchctl print gui/501` again
#
# Since some of these services will be automatically re-enabled at next boot this script exist. So u could:
# Place undesireable system services on list 1 and user services on list 2

# Create a shell script
# Copy/paste to a file at -> /usr/local/bin/
# Rename as -> name.sh
# Set execute permissions -> sudo chmod +x /usr/local/bin/name.sh
# Remove any blocking file attributes -> xattr -cr /usr/local/bin/*
# Set an alias on .zshrc -> alias name="/usr/local/bin/name.sh"
# Run file on terminal -> name

# SIP (Bootout option only)
# SIP must be disabled only when u bootout a service. For example: `launchctl bootout system/com.apple.name`.  
# Bootout will tear them down into little tiny pieces and won't ever comeback.
# When one must bootout. A safer alternative to disable SIP is:  `csrutil enable --without fs`.  The regular way is `csrutil disable` but it also disables the fileSystem (fs), Kernel, and NVRAM





#!/bin/bash
# ~/bin/brew-maintenance.sh

echo ""
echo ".."
echo "Running Ist of 2 tasks"

echo "   ≠≠– launchctl system. √"



sudo launchctl disable system/com.apple.imdpersistence.IMDPersistenceAgent
sudo launchctl disable system/com.apple.wifiFirmwareLoader

sudo launchctl disable system/com.apple.diagnosticextensions.osx.spotlight.helper
sudo launchctl disable system/ccom.apple.assetsubscriptiond
sudo launchctl disable system/com.apple.mobile.obliteration
sudo launchctl disable system/com.apple.devicemanagementclient.managedeventsd

sudo launchctl disable system/com.apple.systempreferences.cacheAssistant
sudo launchctl disable system/com.apple.mediaremoted
sudo launchctl disable system/com.apple.adid
sudo launchctl disable system/com.apple.modelcatalogd
sudo launchctl disable system/com.apple.managedappdistributiond
sudo launchctl disable system/com.vix.cron
sudo launchctl disable system/com.apple.mbusertrampoline
sudo launchctl disable system/com.apple.imdpersistence.IMDPersistenceAgent
sudo launchctl disable system/com.apple.imdpersistence.IMDPersistenceAgent
sudo launchctl disable system/com.apple.imdpersistence.IMDPersistenceAgent
sudo launchctl disable system/com.apple.imdpersistence.IMDPersistenceAgent


sudo launchctl disable system/com.apple.audio.systemsoundserverd
sudo launchctl disable system/com.apple.devicerecoveryd
sudo launchctl disable system/com.apple.RemoteDesktop.PrivilegeProxy
sudo launchctl disable system/com.apple.avbdeviced
sudo launchctl disable system/com.apple.uarpd
sudo launchctl disable system/com.apple.cvmsServ
sudo launchctl disable system/com.apple.diskimagesiod

sudo launchctl disable system/com.apple.accessoryupdaterd
sudo launchctl disable system/com.apple.swiftuitracingsupport.xpc
sudo launchctl disable system/com.apple.diagnosticd
sudo launchctl disable system/com.apple.AssetCacheTetheratorService
sudo launchctl disable system/com.apple.wifivelocityd
sudo launchctl disable system/com.apple.uarpassetmanagerd
sudo launchctl disable system/com.apple.modelmanagerd
sudo launchctl disable system/com.apple.configd

sudo launchctl disable system/com.apple.mobilegestalt.xpc
sudo launchctl disable system/com.apple.installandsetup.systemmigrationd

sudo launchctl disable system/com.apple.BTServer.le
sudo launchctl disable system/com.apple.IOUserBluetoothSerialDriver-0x100001317
sudo launchctl disable system/com.apple.driverkit.AppleUserHIDDrivers-0x100000f96

sudo launchctl disable system/com.apple.captiveagent
sudo launchctl disable system/com.apple.metadata.mds.spindump
sudo launchctl disable system/com.apple.storagekitd
sudo launchctl disable system/com.apple.WirelessRadioManager
sudo launchctl disable system/com.apple.mobileassetd


sudo launchctl disable system/com.apple.audio.AudioComponentRegistrar
sudo launchctl disable system/com.apple.srp-mdns-proxy
sudo launchctl disable system/com.apple.AssetCacheLocatorService
sudo launchctl disable system/com.apple.betaenrollmentd
sudo launchctl disable system/com.apple.dt.automationmode-writer
sudo launchctl disable system/com.apple.netauth.sys.auth
sudo launchctl disable system/com.apple.remoted
sudo launchctl disable system/com.apple.ManagedClient.mechanism
sudo launchctl disable system/com.apple.imdpersistence.IMDPersistenceAgent

sudo launchctl disable system/com.apple.nfsconf
sudo launchctl disable system/com.apple.mobileactivationd
sudo launchctl disable system/com.apple.logd
sudo launchctl disable system/com.apple.mobile.keybagd
sudo launchctl disable system/com.apple.systemadministration.writeconfig
sudo launchctl disable system/com.apple.mobile.storage_mounter_proxy
sudo launchctl disable system/com.apple.aneuserd
sudo launchctl disable system/com.apple.BlueTool

sudo launchctl disable system/com.apple.mobile.softwareupdated
sudo launchctl disable system/com.apple.cmio.videodriverkithostextension
sudo launchctl disable system/com.apple.gamepolicyd
sudo launchctl disable system/com.apple.usbaudiod
sudo launchctl disable system/com.apple.MobileInstallationHelperService
sudo launchctl disable system/com.apple.powerd.swd
sudo launchctl disable system/com.apple.ManagedClient
sudo launchctl disable system/com.apple.cmio.VDCAssistant
sudo launchctl disable system/com.apple.AppleQEMUGuestAgent

sudo launchctl disable system/com.apple.testmanagerd.remote
sudo launchctl disable system/com.apple.xpc.uscwoap
sudo launchctl disable system/com.apple.kernelmanagerd
sudo launchctl disable system/com.apple.AppSSODaemon
sudo launchctl disable system/com.apple.security.authtrampoline
sudo launchctl disable system/com.apple.rpcbind
sudo launchctl disable system/com.apple.printtool.daemon
sudo launchctl disable system/com.apple.audiomxd
sudo launchctl disable system/com.apple.cmio.uvcassistantextension
sudo launchctl disable system/com.apple.RosettaUpdateService
sudo launchctl disable system/com.apple.mdmclient.daemon
sudo launchctl disable system/com.apple.ctkd
sudo launchctl disable system/com.apple.icloud.searchpartyd
sudo launchctl disable system/com.apple.mbsystemadministration
sudo launchctl disable system/com.apple.metadata.mds.index.11B89511-9B21-484E-9F69-61D439ED08F7
sudo launchctl disable system/com.apple.DesktopServicesHelper
sudo launchctl disable system/com.apple.Virtualization.AppleVirtualPlatformHIDBridge

sudo launchctl disable system/com.apple.WindowServer
sudo launchctl disable system/com.apple.netauth.sys.gui
sudo launchctl disable system/com.apple.diskimagesiod.ram
sudo launchctl disable system/com.apple.postfix.newaliases
sudo launchctl disable system/com.apple.ionodecache
sudo launchctl disable system/com.apple.ManagedClient.enroll
sudo launchctl disable system/com.apple.netbiosd
sudo launchctl disable system/com.apple.remotemanagementd
sudo launchctl disable system/com.apple.NetworkSharing
sudo launchctl disable system/com.apple.softwareupdate_firstrun_tasks
sudo launchctl disable system/com.apple.AppSSOAgent.login
sudo launchctl disable system/com.apple.aonsensed
sudo launchctl disable system/com.apple.devicemanagementclient.teslad
sudo launchctl disable system/org.cups.cupsd

sudo launchctl disable system/com.apple.usbmuxd
sudo launchctl disable system/com.apple.dt.RemotePairingDataVaultHelper
sudo launchctl disable system/com.apple.appleh13camerad

sudo launchctl disable system/com.apple.dynamic_pager
sudo launchctl disable system/com.apple.CSCSupportd
sudo launchctl disable system/com.apple.MobileSoftwareUpdate.CleanupPreparePathService
sudo launchctl disable system/com.apple.cloudd
sudo launchctl disable system/com.apple.usbctelemetryd
sudo launchctl disable system/com.apple.powerlogHelperd
sudo launchctl disable system/com.apple.MobileAsset.ManifestStorageService
sudo launchctl disable system/com.apple.backgroundtaskmanagementd
sudo launchctl disable system/com.apple.dasd
sudo launchctl disable system/com.apple.kuncd
sudo launchctl disable system/com.apple.corecaptured
sudo launchctl disable system/com.apple.triald.system
sudo launchctl disable system/com.apple.aned
sudo launchctl disable system/com.apple.coreservices.sharedfilelistd
sudo launchctl disable system/com.apple.scsid
sudo launchctl disable system/com.apple.AssetCacheManagerService
sudo launchctl disable system/com.apple.griddatad

sudo launchctl disable system/com.apple.diskimagesiod.spb
sudo launchctl disable system/com.apple.cmio.iOSScreenCaptureAssistant
sudo launchctl disable system/com.apple.aslmanager
sudo launchctl disable system/com.apple.mobile.usermanagerd
sudo launchctl disable system/com.apple.smb.preferences
sudo launchctl disable system/com.apple.racoon
sudo launchctl disable system/com.apple.msrpc.netlogon
sudo launchctl disable system/com.apple.mobile.storage_mounter
sudo launchctl disable system/com.apple.xartstorageremoted
sudo launchctl disable system/com.apple.RemotePairTool
sudo launchctl disable system/com.apple.cmio.registerassistantservice
sudo launchctl disable system/com.apple.uarphidd



echo ""
echo "Show System Disabled services"
echo " "

launchctl print system | grep 'disabled'










echo ""
echo "......"
echo "Running Ist of 2 tasks"

echo "      ≠≠– launchctl gui/501.  √"


#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent

#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent

#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent

#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent


#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent
#sudo launchctl disable gui/501/com.apple.imdpersistence.IMDPersistenceAgent

























