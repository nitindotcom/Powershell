## PowerShell Script to Retrieve WiFi Password

### Description
This PowerShell script prompts the user to input the name of a WiFi profile and retrieves the password for that profile.

### Usage
1. Run the script in PowerShell.
2. Enter the name of the WiFi profile when prompted.
3. The script will display the password if it's stored for the specified profile.

### Script
```powershell
# Prompt user to input WiFi profile name
$profileName = Read-Host -Prompt "Enter the name of the WiFi profile"

# Get WiFi password
$wifiPassword = netsh wlan show profile name="$profileName" key=clear | Select-String -Pattern "Key Content" | ForEach-Object { $_.ToString().Split(":")[1].Trim() }

# Check if password is found
if ($wifiPassword -ne $null) {
    Write-Output "Password for WiFi Profile '$profileName': $wifiPassword"
} else {
    Write-Output "WiFi Profile '$profileName' not found or password not stored."
}
