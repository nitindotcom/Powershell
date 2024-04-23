# Disk Space Monitor PowerShell Script

## Overview
This PowerShell script retrieves information about the logical disks on a Windows system and calculates the percentage of free space on each disk. It also displays the amount of free space in gigabytes (GB). This script can be useful for monitoring disk space usage on your system.

## Usage
1. Open PowerShell.
2. Copy the following script:
```powershell
$diskInfo = Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property DeviceID, VolumeName, FreeSpace, Size

foreach ($disk in $diskInfo) {
    $deviceID = $disk.DeviceID
    $volumeName = $disk.VolumeName
    $freeSpaceBytes = $disk.FreeSpace
    $totalSpaceBytes = $disk.Size
    
    # Convert bytes to gigabytes
    $freeSpaceGB = [math]::Round($freeSpaceBytes / 1GB, 2)
    
    # Calculate percentage of free space
    $percentageFree = ($freeSpaceBytes / $totalSpaceBytes) * 100
    
    Write-Host "Disk Name: $volumeName (Device ID: $deviceID) - Free Space: $freeSpaceGB GB ($percentageFree% free)"
}
