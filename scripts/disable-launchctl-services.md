```bash
#!/bin/bash

# Disabling Undesireables - or mobile device management related (personal favorites)
# At System and local user levels. A quarantine folder created for System agents/daemons under /Users/shared

# List of launch agents/daemons to disable and quarantine
AGENTS=(
    "com.apple.mediaremoted"
    "com.apple.testmanagerd.remote"
    "com.apple.remoted"
    "com.apple.xartstorageremoted"
    "com.apple.remotemanagementd"
    "com.apple.mediaremoteagent"
    "com.apple.remotecompositorclientd"
    "com.apple.mdmclient.agent"
    "com.apple.managedcorespotlightd"
    "com.apple.managedappdistributionagent"
    "com.apple.managedcorespotlightd.07375B24-6951-CF8F-9E5F-8102D3BD352D"
    "com.apple.translationd"
    "com.apple.SpeechRecognitionCore.brokerd"
    "com.apple.metadata.mdbulkimport"
    "com.apple.WorkflowKit.ShortcutsViewService"
    "com.apple.SetStoreUpdateService"
    "com.apple.mobiledeviceupdater"
    "com.apple.videoconference.camera"
    "com.apple.studentd"
    "com.apple.siriinferenced"
    "com.apple.Maps.mapssyncd"
    "com.apple.SystemUIServer.agent"
    "com.apple.managedappdistributionagent"
    "/System/Library/Templates/Data/Library/Preferences/com.apple.ByteRangeLocking.plist"
    "/System/Library/Templates/Data/Library/Preferences/com.apple.security.appsandbox.plist"
    "/System/Library/Templates/Data/Library/Preferences/com.apple.Boot.plist"
    "/System/Library/Templates/Data/Library/Preferences/Logging/Subsystems/com.apple.WebBookmarks.plist"
    "/System/Library/Templates/Data/Library/Preferences/Logging/Subsystems/com.apple.WebInspector.plist"
 
)

echo "Processing all listed agents..."

for AGENT in "${AGENTS[@]}"; do
    echo "Disabling $AGENT..."

    # Disable for current user
    launchctl disable "user/$(id -u)/$AGENT" 2>/dev/null

    # Disable at system level
    sudo launchctl disable "system/$AGENT" 2>/dev/null

    # Attempt to locate the binary path
    plist_path=$(launchctl print system/$AGENT 2>/dev/null | grep 'path = ' | awk -F'= ' '{print $2}')
    if [[ -n "$plist_path" && -f "$plist_path" ]]; then
        echo "Quarantining $plist_path"
        sudo xattr -w com.apple.quarantine "blocked" "$plist_path" 2>/dev/null
        sudo chmod 000 "$plist_path" 2>/dev/null
    else
        echo "Binary for $AGENT not found or inaccessible"
    fi

    echo "$AGENT processed."
done

echo "All agents processed."






```
