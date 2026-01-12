```bash

#!/bin/bash

# Create a shell script
# Copy/paste to a file at -> /usr/local/bin/
# Rename as -> name.sh
# Set execute permissions -> sudo chmod +x /usr/local/bin/name.sh
# Remove any blocking file attributes -> xattr -cr /usr/local/bin/*
# Set an alias on .zshrc -> alias name="/usr/local/bin/name.sh"
# Run file on terminal -> name

# SIP disabled not required with this approach.


# === CONFIGURATION ===
# List all full paths to apps you want to quarantine
APPS_TO_QUARANTINE=(
"/System/Library/Templates/Data/Library/Application Support/Script Editor/Templates/Cocoa-AppleScript Applet.app"
"/System/Library/Templates/Data/Library/Application Support/Script Editor/Templates/Droplets/Recursive Image File Processing Droplet.app"
"/System/Library/Templates/Data/Library/Application Support/Script Editor/Templates/Droplets/Droplet with Settable Properties.app"
"/System/Library/Templates/Data/Library/Application Support/Script Editor/Templates/Droplets/Recursive File Processing Droplet.app"

"/System/Library/Templates/Data/Library/CoreServices/Applications/Folder Actions Setup.app"
"/System/Library/Templates/Data/Library/CoreServices/Applications/Ticket Viewer.app"
"/System/Library/Templates/Data/Library/CoreServices/Applications/Feedback Assistant.app"
"/System/Library/Templates/Data/Library/CoreServices/Applications/IOS App Installer.app"
"/System/Library/Templates/Data/Library/CoreServices/Applications/Desk View.app"
"/System/Library/Templates/Data/Library/CoreServices/AddressBookUrlForwarder.app"

"/System/Library/Templates/Data/Library/CoreServices/AddressBookUrlForwarder.app"
"/System/Library/Templates/Data/Library/CoreServices/iCloud.app"
"/System/Library/Templates/Data/Library/CoreServices/com.apple.launchservices.lsd.cscdb"
"/System/Library/Templates/Data/Library/CoreServices/RemoteManagement/AppleVNCServer.bundle"
"/System/Library/Templates/Data/Library/CoreServices/RemoteManagement/ARDAgent.app"
"/System/Library/Templates/Data/Library/CoreServices/RemoteManagement/Remote Desktop Message.app"
"/System/Library/Templates/Data/Library/CoreServices/RemoteManagement/ScreensharingAgent.bundle"
"/System/Library/Templates/Data/Library/CoreServices/RemoteManagement/screensharingd.bundle"
"/System/Library/Templates/Data/Library/CoreServices/RemoteManagement/SSMenuAgent.app"

"/System/Library/Templates/Data/Library/CoreServices/CSUserAgent"

"/System/Library/Templates/Data/Library/CoreServices/CommonCocoaPanels.bundle"
"/System/Library/Templates/Data/Library/CoreServices/InstallAssistantCompatibility.bundle"
"/System/Library/Templates/Data/Library/CoreServices/diagnostics_agent"
"/System/Library/Templates/Data/Library/CoreServices/diagnosticservicesd"
"/System/Library/Templates/Data/Library/CoreServices/FolderActionsDispatcher.app"
"/System/Library/Templates/Data/Library/CoreServices/InternetSharing.bundle"

"/System/Library/Templates/Data/Library/CoreServices/KeyboardAccessAgent.app"
"/System/Library/Templates/Data/Library/CoreServices/ManagedClient.app"
"/System/Library/Templates/Data/Library/CoreServices/mapspushd"
"/System/Library/Templates/Data/Library/CoreServices/NetAuthAgent.app"

"/System/Library/Templates/Data/Library/CoreServices/appplaceholdersyncd"
"/System/Library/Templates/Data/Library/CoreServices/Captive Network Assistant.app"

"/System/Library/Templates/Data/Library/CoreServices/InstallAssistantCompatibility.bundle"
"/System/Library/Templates/Data/Library/CoreServices/InternetSharing.bundle"
"/System/Library/Templates/Data/Library/CoreServices/RemotePairTool"
"/System/Library/Templates/Data/Library/CoreServices/RestoreVersion.plist"

"/System/Library/Templates/Data/Library/CoreServices/Paired Devices.app"
"/System/Library/Templates/Data/Library/CoreServices/Keychain Circle Notification.app"
"/System/Library/Templates/Data/Library/CoreServices/KeyboardSetupAssistant.app"
"/System/Library/Templates/Data/Library/CoreServices/pbs"
"/System/Library/Templates/Data/Library/CoreServices/SubmitDiagInfo"
"/System/Library/Templates/Data/Library/CoreServices/SystemUIServer.app"

"/System/Library/Templates/Data/Library/CoreServices/ThermalTrap.app"
"/System/Library/Templates/Data/Library/CoreServices/UniversalAccessControl.app"
"/System/Library/Templates/Data/Library/CoreServices/VoiceOver.app"
"/System/Library/Templates/Data/Library/CoreServices/StageManagerOnboarding.app"
"/System/Library/Templates/Data/Library/CoreServices/Script Menu.app"
"/System/Library/Templates/Data/Library/CoreServices/uncd"
"/System/Library/Templates/Data/Library/CoreServices/rcd.app"
"/System/Library/Templates/Data/Library/CoreServices/rc.trampoline"
"/System/Library/Templates/Data/Library/CoreServices/ShortcutsActions.app"
"/System/Library/Templates/Data/Library/CoreServices/ShortcutsEvents.app"
"/System/Library/Templates/Data/Library/CoreServices/ShortcutDroplet.app"
"/System/Library/Templates/Data/Library/CoreServices/sharedfilelistd"
"/System/Library/Templates/Data/Library/CoreServices/osanalyticshelper"
"/System/Library/Templates/Data/Library/CoreServices/ScopedBookmarkAgent"
"/System/Library/Templates/Data/Library/CoreServices/ionodecache"
"/System/Library/Templates/Data/Library/CoreServices/RegisterPluginIMApp.app"
"/System/Library/Templates/Data/Library/CoreServices/Certificate Assistant.app"
"/System/Library/Templates/Data/Library/CoreServices/KernelEventAgent.bundle"
"/System/Library/Templates/Data/Library/CoreServices/BluetoothUIServer.app"
"/System/Library/Templates/Data/Library/CoreServices/Captive Network Assistant.app"
"/System/Library/Templates/Data/Library/CoreServices/Bluetooth Setup Assistant.app"
"/System/Library/Templates/Data/Library/CoreServices/Image Events.app"

"/System/Library/Templates/Data/Library/CoreServices/CSUserAgent"
"/System/Library/Templates/Data/Library/CoreServices/CloudSettingsSyncAgent"
"/System/Library/Templates/Data/Library/CoreServices/Rosetta 2 Updater.app"

"/System/Library/AssetsV2/com_apple_MobileAsset_*"





"/System/Library/Core Services/Automator Application Stub.app"
"/opt/homebrew/Cellar/python@3.14/3.14.0_1/IDLE 3.app"
"/opt/homebrew/var/homebrew/tmp/.cellar/python@3.14/3.14.0_1/IDLE 3.app"
"/System/Library/CoreServices/RemoteManagement/ARDAgent.app"
"/System/Library/CoreServices/RemoteManagement/Remote Desktop Message.app"
"/System/Library/CoreServices/RemoteManagement/SSMenuAgent.app"
"/System/Library/CoreServices/Automator Application Stub.app"

"/System/Library/CoreServices/Bluetooth Setup Assistant.app"

"/System/Library/CoreServices/BluetoothUIServer.app"
"/System/Library/CoreServices/BluetoothUIService.app"
"/System/Library/CoreServices/Captive Network Assistant.app"
"/System/Library/CoreServices/Certificate Assistant.app"

"/System/Library/CoreServices/CoreServicesUIAgent.app"
"/System/Library/CoreServices/Database Events.app"
"/System/Library/CoreServices/FamilyExtensionHost.app"

"/System/Library/CoreServices/FolderActionsDispatcher.app"
"/System/Library/CoreServices/KeyboardAccessAgent.app"
"/System/Library/CoreServices/Keychain Circle Notification.app"
"/System/Library/CoreServices/loginwindow.app"
"/System/Library/CoreServices/ManagedClient.app"
"/System/Library/CoreServices/NetAuthAgent.app"
"/System/Library/CoreServices/rcd.app"
"/System/Library/CoreServices/RegisterPluginIMApp.app"
"/System/Library/CoreServices/ShortcutsActions.app"
"/System/Library/CoreServices/SystemUIServer.app"
"/System/Library/CoreServices/VoiceOver.app"
"/System/Library/CoreServices/TextInputSwitcher.app"
"/System/Library/CoreServices/SystemIntents.app"
"/System/Library/CoreServices/Shortcuts Events.app"
"/System/Library/CoreServices/ShortcutDroplet.app"
"/System/Library/CoreServices/Ticket Viewer.app"
"/System/Library/CoreServices/Applications/iOS App Installer.app"

)

# Quarantine folder (safe location)
QUARANTINE_DIR="/Users/Shared/Quarantine"

# === SCRIPT START ===
echo "[*] Creating quarantine folder..."
sudo mkdir -p "$QUARANTINE_DIR"
sudo chmod 700 "$QUARANTINE_DIR"

for APP in "${APPS_TO_QUARANTINE[@]}"; do
    if [ -d "$APP" ]; then
        APP_NAME=$(basename "$APP")
        DEST="$QUARANTINE_DIR/$APP_NAME"

        echo "[*] Quarantining: $APP_NAME"
        sudo cp -R "$APP" "$DEST"

        # Remove execute permissions on binaries inside the app bundle
        sudo find "$DEST" -type f -perm +111 -exec chmod -x {} \;

        echo "[*] $APP_NAME quarantined at $DEST"
     fi


     if [ -d "$APP" ]; then
        APP_NAME=$(basename "$PLIST")
        DEST="$QUARANTINE_DIR/$APP_NAME"

        echo "[*] Quarantining: $APP_NAME"
        sudo cp -R "$APP" "$DEST"

        # Remove execute permissions on binaries inside the app bundle
        sudo find "$DEST" -type f -perm +111 -exec chmod -x {} \;

        echo "[*] $APP_NAME quarantined at $DEST"

    else
        echo "[!] App not found: $APP"
    fi

done

# Make quarantine folder immutable
sudo chflags uchg "$QUARANTINE_DIR"
echo "[*] Quarantine folder set immutable. To modify, use 'sudo chflags nouchg $QUARANTINE_DIR'"

echo "[*] Quarantine complete."










:100:

```
