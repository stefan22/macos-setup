```bash

#!/usr/bin/env bash
set -e
#
# I. Wi-Fi Only
# -----------------------------------------------------------------------
# This script installs a networklock on /usr/local/bin
# It creates a 'launchd plist' file that runs at boot
# It sets a strict 'PF firewall' allowing only Wi-fi traffic on 'en0'
# Its fully persistent and safe (it doesnt touch system interfaces)
#
#
# II. Create a shell script
# -----------------------------------------------------------------------
# Copy/paste to a file at -> /usr/local/bin/
# Rename as -> name.sh
# Set execute permissions -> sudo chmod +x /usr/local/bin/name.sh
# Remove any blocking file attributes -> xattr -cr /usr/local/bin/*
# Set an alias on .zshrc -> alias name="/usr/local/bin/name.sh"
# Run file on terminal -> name
# -----------------------------------------------------------------------
#
#


SCRIPT_PATH="/usr/local/bin/network-lock.sh"
PLIST_PATH="/Library/LaunchDaemons/com.user.networklock.plist"
PF_ANCHOR="/etc/pf.anchors/network-lock.rules"

echo "▶ Installing network-lock script..."

# -------------------------
# Write network-lock.sh
# -------------------------
sudo tee "$SCRIPT_PATH" > /dev/null <<'EOF'
#!/usr/bin/env bash
set -e

echo "▶ Enforcing network configuration (Wi-Fi en0 only)"

# -------------------------
# Sanity check
# -------------------------
if ! ifconfig en0 >/dev/null 2>&1; then
  echo "❌ en0 not found. Aborting."
  exit 1
fi

# -------------------------
# Enable Wi-Fi (en0)
# -------------------------
echo "▶ Enabling Wi-Fi on en0"
networksetup -setairportpower en0 on

# -------------------------
# Disable all other hardware network services
# -------------------------
echo "▶ Disabling other network services..."
while IFS= read -r service; do
  [[ "$service" == *Wi-Fi* ]] && continue
  echo "  - Disabling service: $service"
  networksetup -setnetworkserviceenabled "$service" off || true
done < <(networksetup -listallnetworkservices | tail -n +2)

# -------------------------
# Disable IPv6 on Wi-Fi
# -------------------------
echo "▶ Disabling IPv6 on Wi-Fi"
networksetup -setv6off "Wi-Fi"

# -------------------------
# Force Wi-Fi as primary service
# -------------------------
echo "▶ Forcing Wi-Fi as primary service"
networksetup -ordernetworkservices "Wi-Fi"

# -------------------------
# DNS cleanup
# -------------------------
echo "▶ Clearing DNS settings for Wi-Fi"
networksetup -setdnsservers "Wi-Fi" empty
networksetup -setsearchdomains "Wi-Fi" empty

# -------------------------
# Flush DNS & caches
# -------------------------
echo "▶ Flushing DNS caches"
dscacheutil -flushcache
killall -HUP mDNSResponder || true
killall mDNSResponderHelper || true

# -------------------------
# Show network status
# -------------------------
echo "▶ Current network configuration:"
networksetup -getinfo "Wi-Fi"
networksetup -getdnsservers "Wi-Fi"

echo "✔ Network lockdown complete"
EOF

sudo chmod +x "$SCRIPT_PATH"
sudo chown root:wheel "$SCRIPT_PATH"

echo "▶ Creating launchd plist at $PLIST_PATH..."

# -------------------------
# Write launchd plist
# -------------------------
sudo tee "$PLIST_PATH" > /dev/null <<EOF
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>com.user.networklock</string>

    <key>ProgramArguments</key>
    <array>
      <string>$SCRIPT_PATH</string>
    </array>

    <key>RunAtLoad</key>
    <true/>

    <key>StandardErrorPath</key>
    <string>/var/log/network-lock.err</string>
    <key>StandardOutPath</key>
    <string>/var/log/network-lock.log</string>
  </dict>
</plist>
EOF

sudo chown root:wheel "$PLIST_PATH"
sudo chmod 644 "$PLIST_PATH"
sudo launchctl load "$PLIST_PATH"

echo "▶ Creating strict PF rules at $PF_ANCHOR..."

# -------------------------
# Write PF rules
# -------------------------
sudo tee "$PF_ANCHOR" > /dev/null <<'EOF'
# Block all by default
block all

# Allow local loopback
set skip on lo0

# Allow Wi-Fi en0 outbound
pass out on en0 inet

# Allow established inbound traffic for Wi-Fi
pass in on en0 inet proto tcp from any to any keep state
pass in on en0 inet proto udp from any to any keep state
EOF

# Include anchor in pf.conf if not already present
if ! grep -q "network-lock" /etc/pf.conf; then
  echo "anchor \"network-lock\"" | sudo tee -a /etc/pf.conf
  echo "load anchor \"network-lock\" from \"$PF_ANCHOR\"" | sudo tee -a /etc/pf.conf
fi

# Enable PF
sudo pfctl -f /etc/pf.conf
sudo pfctl -e || true

echo "✔ Network-lock setup complete."
echo "✔ Script will run at boot and PF firewall is enabled (Wi-Fi only)."


```


:100:
