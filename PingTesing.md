# Server Ping Script

This PowerShell script allows you to ping multiple servers to check if they are reachable or not.

## Usage

1. Open the PowerShell console.
2. Navigate to the directory where the script is located.
3. Run the script by typing `.\ping_servers.ps1` and pressing Enter.
4. The script will ping each server specified in the list and display whether it is reachable or not.

## Configuration

You can modify the list of servers to ping by editing the `$servers` array in the script. Add or remove server names or IP addresses as needed.

## Example

```powershell
# List of servers to ping
$servers = "server1", "server2", "server3"

# Loop through each server and ping it
foreach ($server in $servers) {
    $pingResult = Test-Connection -ComputerName $server -Count 1 -ErrorAction SilentlyContinue
    if ($pingResult -ne $null) {
        Write-Host "$server is reachable."
    } else {
        Write-Host "$server is not reachable."
    }
}
