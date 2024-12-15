# Praktikum 13 aruanne

Selles praktikumis tegelesin Windowsis skriptimisega. Oli raskem kui Linuxi oma ja rohkem aeganõudev.

Skripti väljundi fail:
https://github.com/user-attachments/files/18140400/output.txt

Skript ise.
1.     # Faili algus
       $outputFile = "output.txt"

       # Tühjendame faili alguses
       Clear-Content -Path $outputFile -ErrorAction SilentlyContinue

       # Masina nimi, PowerShelli versioon ja Windowsi versioon
       "Masina info:" | Out-File -FilePath $outputFile -Append
       "Masina nimi: $(hostname)" | Out-File -FilePath $outputFile -Append
       "PowerShelli versioon: $($PSVersionTable.PSVersion)" | Out-File - 
       FilePath $outputFile -Append
       "Windowsi versioon: 
       $([System.Environment]::OSVersion.VersionString)" | Out-File - 
       FilePath 
       $outputFile -Append
       "" | Out-File -FilePath $outputFile -Append

       # Võrgu konfiguratsioon
       # Saab infot võrguadapterite kohta, kus IP on lubatud
       "Võrgu konfiguratsioon:" | Out-File -FilePath $outputFile -Append
       $networkInfo = Get-WmiObject Win32_NetworkAdapterConfiguration - 
       Filter "IPEnabled='True'"
       foreach ($adapter in $networkInfo) {
           "MAC-aadress: $($adapter.MACAddress)" | Out-File -FilePath 
       $outputFile -Append
           "IP-aadress: $($adapter.IPAddress -join ', ')" | Out-File - 
       FilePath $outputFile -Append
           "Võrgumask: $($adapter.IPSubnet -join ', ')" | Out-File - 
       FilePath $outputFile -Append
           "Vaikelüüsi aadress: $($adapter.DefaultIPGateway -join ', ')" | 
       Out-File -FilePath $outputFile -Append
           "DHCP lubatud: $($adapter.DHCPEnabled)" | Out-File -FilePath 
       $outputFile -Append
           "" | Out-File -FilePath $outputFile -Append
       }

       # Arvuti protsessor ja RAM
       "Arvuti riistvara:" | Out-File -FilePath $outputFile -Append
       $systemInfo = Get-WmiObject Win32_ComputerSystem
       "Protsessori kirjeldus: $($systemInfo.Manufacturer) 
       $($systemInfo.Model)" | Out-File -FilePath $outputFile -Append
       "Põhimälu RAM: $([math]::Round($systemInfo.TotalPhysicalMemory / 
       1GB, 2)) GB" | Out-File -FilePath $outputFile -Append
       "" | Out-File -FilePath $outputFile -Append

       # Graafikakaardi info
       "Graafikakaardi info:" | Out-File -FilePath $outputFile -Append
       $videoController = Get-WmiObject Win32_VideoController
       foreach ($vc in $videoController) {
           "Graafikakaart: $($vc.Name)" | Out-File -FilePath $outputFile - 
           Append
           "Draiveri versioon: $($vc.DriverVersion)" | Out-File -FilePath 
       $outputFile -Append
           "Draiveri kuupäev: $($vc.DriverDate)" | Out-File -FilePath 
       $outputFile -Append
           "Ekraani lahutus: 
       $($vc.CurrentHorizontalResolution)x$($vc.CurrentVerticalResolution)" 
       | Out-File -FilePath $outputFile -Append
           "" | Out-File -FilePath $outputFile -Append
       }

       # Kõvaketta info
       "Arvuti kõvaketaste info:" | Out-File -FilePath $outputFile -Append
       $disks = Get-WmiObject Win32_LogicalDisk -Filter "DriveType=3"
       foreach ($disk in $disks) {
           "Ketas $($disk.DeviceID):" | Out-File -FilePath $outputFile -Append
           "Kogumaht: $([math]::Round($disk.Size / 1GB, 2)) GB" | Out-File -
       FilePath $outputFile -Append
           "Vaba ruum: $([math]::Round($disk.FreeSpace / 1GB, 2)) GB" | Out-File -
       FilePath $outputFile -Append
           "" | Out-File -FilePath $outputFile -Append
       }

       # PCI seadmed
       # Kuvab PCI-siinil olevate seadmete info (nime, tootja, draiveri versioon)
       "PCI-siinil olevad seadmed:" | Out-File -FilePath $outputFile -Append
       $pciDevices = Get-WmiObject Win32_PnPEntity | Where-Object { 
       $_.PNPClass -eq "System" }
       foreach ($device in $pciDevices) {
           "Seade: $($device.Name)" | Out-File -FilePath $outputFile -Append
           "Tootja: $($device.Manufacturer)" | Out-File -FilePath $outputFile -Append
           "Draiveri versioon: $($device.DriverVersion)" | Out-File -FilePath $outputFile -Append
       "" | Out-File -FilePath $outputFile -Append
       }

       # Arvuti kasutajad
       "Arvutis olevad kasutajad:" | Out-File -FilePath $outputFile -Append
        $users = Get-WmiObject Win32_UserAccount -Filter "LocalAccount='True'"
       foreach ($user in $users) {
           "Kasutajanimi: $($user.Name)" | Out-File -FilePath $outputFile -Append
           "Kirjeldus: $($user.Description)" | Out-File -FilePath $outputFile -Append
           "Lokaalne: $($user.LocalAccount)" | Out-File -FilePath $outputFile -Append
           "Keelatud: $($user.Disabled)" | Out-File -FilePath $outputFile -Append
           "" | Out-File -FilePath $outputFile -Append
       }

       # Käimasolevate protsesside arv
       "Käimasolevate protsesside info:" | Out-File -FilePath $outputFile -Append
       "Protsesside koguarv: $(Get-Process | Measure-Object).Count" | Out- 
       File -FilePath $outputFile -Append

       # 10 viimasena käivitatud protsessi
       "10 viimast käivitatud protsessi:" | Out-File -FilePath $outputFile -Append
       $recentProcesses = Get-Process |
           Where-Object { $_.StartTime -ne $null } |
           Sort-Object StartTime -Descending |
           Select-Object -First 10 Name, Id, StartTime
       $recentProcesses | Format-Table | Out-String | Out-File -FilePath 
       $outputFile -Append

       # Kuupäev ja kellaaeg
       "Arvuti kuupäev ja kellaaeg:" | Out-File -FilePath $outputFile -Append
       (Get-Date).ToString() | Out-File -FilePath $outputFile -Append
