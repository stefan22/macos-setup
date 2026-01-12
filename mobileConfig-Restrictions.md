
## Applying MobileConfig Restrictions Settings in MacOS

 <br />
 This is probably the most reliable way to enforce or make sure your settings will persist system-wide in MacOS.       
  <br /><br />
  
 This profile sets a group of restrictions to your machine along with a profile removal policy `removeProfilePassword`. Add or remove Restrictions and set your Profile Removal password below.
 
 It is also possible to change the scope for the Profile using the `Payload Scope` key. Options are 'System' or 'User'.       
 If for some reason some of the restrictions settings are not being enforced, it is likely because the restriction may no longer applied to MacOS devices (or perhaps the setting is only available on IOS
 devices) and/or its policy may have been updated, so look for "`Device Managment Restrictions for MacOS`" online to make sure the correct restriction is being set.
 <br />
 
 **Copy/paste** the the xml code below to a file in your computer and save it as **profileName.mobileconfig**. Then go to System Settings > General > Device Management and upload the file to your computer.



<br /><br />         

```bash
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>HasRemovalPasscode</key>
	<true/>
	<key>PayloadContent</key>
	<array>
		<dict>
			<key>PayloadDescription</key>
			<string>Configures restrictions</string>
			<key>PayloadDisplayName</key>
			<string>Restrictions Mint2</string>
			<key>PayloadIdentifier</key>
			<string>com.apple.applicationaccess.DCADE8C3-C920-4814-9FA9-546C0D92E402</string>
			<key>PayloadType</key>
			<string>com.apple.applicationaccess</string>
			<key>PayloadUUID</key>
			<string>DCADE8C3-C920-4814-9FA9-546C0D92E402</string>
			<key>PayloadVersion</key>
			<integer>1</integer>
			<key>ActivityBTLESharingEnabled</key>
			<false/>
			<key>ActivityReceivingAllowed</key>
			<false/>
			<key>ClipboardSharingEnabled</key>
			<false/>
			<key>GKFeatureGameCenterAllowed</key>
			<false/>
			<key>allowAccountModification</key>
			<false/>
			<key>allowExternalIntelligenceIntegrations</key>
			<false/>
			<key>IDEProhibitOnDeviceModelInteraction</key>
			<false/>
			<key>IDEProhibitRemoteModelInteraction</key>
			<false/>
			<key>allowAddingGameCenterFriends</key>
			<false/>
			<key>allowAirDrop</key>
			<false/>
			<key>allowAirPlayIncomingRequests</key>
			<false/>
			<key>allowAirPrint</key>
			<false/>
			<key>allowAirPrintCredentialsStorage</key>
			<false/>
			<key>allowAirPrintiBeaconDiscovery</key>
			<false/>
			<key>allowAppCellularDataModification</key>
			<false/>
			<key>allowAppClips</key>
			<false/>
			<key>allowAppInstallation</key>
			<true/>
			<key>allowAppRemoval</key>
			<true/>
			<key>allowApplePersonalizedAdvertising</key>
			<false/>
			<key>allowAssistant</key>
			<false/>
			<key>allowAssistantUserGeneratedContent</key>
			<false/>
			<key>allowAssistantWhileLocked</key>
			<false/>
			<key>allowAutomaticAppDownloads</key>
			<false/>
			<key>allowBTLE</key>
			<false/>
			<key>allowBTLEInstallation</key>
			<false/>
			<key>allowBluetoothModification</key>
			<true/>
			<key>allowCellularPlan</key>
			<false/>
			<key>allowCellularPlanModification</key>
			<false/>
			<key>allowCloudBackup</key>
			<true/>
			<key>allowCloudPhotoLibrary</key>
			<true/>
			<key>allowContinuousPathKeyboard</key>
			<false/>
			<key>allowDeviceNameModification</key>
			<false/>
			<key>allowDictation</key>
			<false/>
			<key>allowESIMModification</key>
			<false/>
			<key>allowESIMOutgoingTransfers</key>
			<false/>
			<key>allowEnablingRestrictions</key>
			<true/>
			<key>allowEnterpriseAppTrust</key>
			<false/>
			<key>allowEnterpriseBookBackup</key>
			<false/>
			<key>allowEnterpriseBookMetadataSync</key>
			<false/>
			<key>allowEraseContentAndSettings</key>
			<true/>
			<key>allowExplicitContent</key>
			<true/>
			<key>allowFilesNetworkDriveAccess</key>
			<false/>
			<key>allowFindMyDevice</key>
			<true/>
			<key>allowFindMyFriends</key>
			<false/>
			<key>allowFindMyFriendsModification</key>
			<false/>
			<key>allowFingerprintForUnlock</key>
			<true/>
			<key>allowFingerprintModification</key>
			<false/>
			<key>allowGameCenter</key>
			<false/>
			<key>allowGlobalBackgroundFetchWhenRoaming</key>
			<false/>
			<key>allowHostPairing</key>
			<false/>
			<key>allowImageGeneration</key>
			<false/>
			<key>allowInAppPurchases</key>
			<true/>
			<key>allowKeyboardShortcuts</key>
			<false/>
			<key>allowMarketplaceAppInstallation</key>
			<false/>
			<key>allowMultiplayerGaming</key>
			<false/>
			<key>allowNotificationsModification</key>
			<false/>
			<key>allowOTAPKIUpdates</key>
			<false/>
			<key>allowPairedWatch</key>
			<false/>
			<key>allowPassbookWhileLocked</key>
			<false/>
			<key>allowPasswordAutoFill</key>
			<true/>
			<key>allowPasswordProximityRequests</key>
			<false/>
			<key>allowPasswordSharing</key>
			<false/>
			<key>allowPersonalHotspotModification</key>
			<false/>
			<key>allowPodcasts</key>
			<false/>
			<key>allowProximitySetupToNewDevice</key>
			<false/>
			<key>allowRadioService</key>
			<false/>
			<key>allowRemoteAppPairing</key>
			<false/>
			<key>allowRemoteScreenObservation</key>
			<false/>
			<key>allowSafari</key>
			<true/>
			<key>allowScreenShot</key>
			<true/>
			<key>allowSharedStream</key>
			<false/>
			<key>allowSpellCheck</key>
			<false/>
			<key>allowSpotlightInternetResults</key>
			<false/>
			<key>allowSystemAppRemoval</key>
			<true/>
			<key>allowUIAppInstallation</key>
			<true/>
			<key>allowUIConfigurationProfileInstallation</key>
			<true/>
			<key>allowUntrustedTLSPrompt</key>
			<false/>
			<key>allowVPNCreation</key>
			<true/>
			<key>allowWallpaperModification</key>
			<true/>
			<key>forceAirDropUnmanaged</key>
			<true/>
			<key>forceAirPrintTrustedTLSRequirement</key>
			<true/>
			<key>forceAssistantProfanityFilter</key>
			<false/>
			<key>forceAuthenticationBeforeAutoFill</key>
			<true/>
			<key>forceAutomaticDateAndTime</key>
			<true/>
			<key>forceClassroomAutomaticallyJoinClasses</key>
			<false/>
			<key>forceClassroomUnpromptedAppAndDeviceLock</key>
			<false/>
			<key>forceClassroomUnpromptedScreenObservation</key>
			<false/>
			<key>forceDelayedSoftwareUpdates</key>
			<false/>
			<key>forceEncryptedBackup</key>
			<true/>
			<key>forceITunesStorePasswordEntry</key>
			<true/>
			<key>forceLimitAdTracking</key>
			<true/>
			<key>forcePreserveESIMOnErase</key>
			<false/>
			<key>forceWatchWristDetection</key>
			<true/>
			<key>forceWiFiPowerOn</key>
			<false/>
			<key>forceWiFiWhitelisting</key>
			<false/>
			<key>ratingRegion</key>
			<string>gb</string>
			<key>restrictFindMyFriends</key>
			<true/>
			<key>safariAcceptCookies</key>
			<real>1.5</real>
			<key>safariAllowAutoFill</key>
			<false/>
			<key>safariAllowJavaScript</key>
			<true/>
			<key>safariAllowPopups</key>
			<false/>
			<key>safariForceFraudWarning</key>
			<true/>
			<key>allowMediaSharing</key>
			<false/>
			<key>allowWritingTools</key>
			<false/>
			<key>allowImagePlayground</key>
			<false/>
			<key>allowGenmoji</key>
			<false/>
			<key>allowIphoneMirroring</key>
			<false/>
			<key>modifyDictation</key>
			<false/>
		</dict>
		<dict>
			<key>PayloadDescription</key>
			<string>Configures a password for profile removal</string>
			<key>PayloadDisplayName</key>
			<string>Profile Removal</string>
			<key>PayloadIdentifier</key>
			<string>com.apple.profileRemovalPassword.4A6C62E0-C911-4066-97F5-05307604FDB2</string>
			<key>PayloadType</key>
			<string>com.apple.profileRemovalPassword</string>
			<key>PayloadUUID</key>
			<string>4A6C62E0-C911-4066-97F5-05307604FDB2</string>
			<key>PayloadVersion</key>
			<integer>1</integer>
			<key>RemovalPassword</key>
			<string>removeProfilePassword</string>
		</dict>
	</array>
	<key>PayloadDisplayName</key>
	<string>Mint92</string>
	<key>PayloadIdentifier</key>
	<string>SMMin.9BAA2CD6-AABA-4F52-A240-68FCFDFA8E7B</string>
	<key>PayloadRemovalDisallowed</key>
	<true/>
	<key>PayloadType</key>
	<string>Configuration</string>
	<key>PayloadScope</key>
	<string>System</string>
	<key>PayloadUUID</key>
	<string>A44458B5-AA6B-4928-B40B-199DE184A933</string>
	<key>PayloadVersion</key>
	<integer>1</integer>
</dict>
</plist>


```

:100:
