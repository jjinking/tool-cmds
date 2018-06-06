# Modifying firewall configs via terminal

```bash
# get current firewall settings
sudo defaults read /Library/Preferences/com.apple.alf globalstate

# turn firewall off
sudo defaults write /Library/Preferences/com.apple.alf globalstate -int 0

# turn firewall on
sudo defaults write /Library/Preferences/com.apple.alf globalstate -int 1
sudo launchctl unload /System/Library/LaunchDaemons/com.apple.alf.agent.plist
sudo launchctl load /System/Library/LaunchDaemons/com.apple.alf.agent.plist

# Rename binary
sudo mv java java.bak

# Update jamf
sudo jamf policy -trigger updateUserInfo

# Put binary back
sudo mv java.bak java
```
