# wmi sample commands


Test-Connection -Count 1 -ComputerName 192.168.0.220

``Get-WmiObject -Namespace "root\cimv2" -Class Win32_LogicalDisk -ComputerName 192.168.0.220 -Credential enbiya``

``Get-WmiObject -Namespace "root\cimv2" -Class Win32_LogicalDisk -ComputerName 192.168.0.220 -Credential enbiya``

``wmic /user:enbiya /password:6161 /node:192.168.0.220 bios get serialnumber``

``Get-WmiObject -Namespace Root -Class __Namespace -ComputerName 192.168.0.220 | Select-Object -Property Name``

## Remote WMI command execution
```
$remoteip = "192.168.0.220"
$username = "enbiya"
$password = ConvertTo-SecureString "6161" -AsPlainText -Force
$Credentials = New-Object -Typename System.Management.Automation.PSCredential -ArgumentList $username, $password

Get-WmiObject -ComputerName $remoteip -Credential $Credentials -Class Win32_VideoController -Namespace "root\cimv2" 
Get-WmiObject -ComputerName $remoteip -Credential $Credentials -Namespace "root\cimv2" -Query "SELECT Name, FreeSpace, Purpose FROM Win32_Volume"
Get-WmiObject -ComputerName $remoteip -Credential $Credentials -Namespace "root\cimv2" -Class win32_bios
Get-WmiObject -ComputerName $remoteip -Credential $Credentials -Class win32_bios | Select-Object -Property SerialNumber
Get-WmiObject -ComputerName $remoteip -Credential $Credentials -Namespace "root\cimv2" -Query "SELECT Name, FreeSpace, Purpose FROM Win32_Volume"
Get-WmiObject -ComputerName $remoteip -Credential $Credentials -Class win32_bios | Convertto-csv
Get-WmiObject -ComputerName $remoteip -Credential $Credentials -Class win32_bios | Convertto-json
```

