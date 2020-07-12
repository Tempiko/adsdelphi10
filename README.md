# adsdelphi10
Delphi 10 with Advanced Database

## Installation Windows 10:

- Clean %temp% - Directory

- Start "Installing Advantage Delphi Components v12"

- Stop at SAP - welcome screen, Go to %Temp% - Directory, enter new created install directory:
- Open powershell in created directory

    ```msiexec /a "Advantage Delphi Components v12.0.msi" /qb TARGETDIR=C:\adsdelphi\files```

- ignore adslocal.cfg errors

- Cancel the installation

- Edit adslocal.cfg, set ANSI_CHAR_SET and OEM_CHAR_SET to match your collation:

    ```notepad c:\adsdelphi\files\System32\adslocal.cfg```


- Open Powershell as Administrator

- Delete all BPI and BPL files in "c:\adsdelphi\files\System32\":

    ```del "c:\adsdelphi\files\System32\*.bpl"```
    ```del "c:\adsdelphi\files\System32\*.bpi"```


- Copy System32 folder to Windows\System32 (Win32 systems) or Windows\SysWOW64 (Win64 systems):
    - Windows 32-Bit: 

    ```copy c:\adsdelphi\files\System32\*.* C:\Windows\System32\```
 
     - Windows 64-Bit: 

    ```copy c:\adsdelphi\files\System32\*.* C:\Windows\SysWOW64\```


- Copy the content of c:\adsdelphi\files\program files to your program files(x86):
    ```Copy-Item -Recurse -Path "C:\adsdelphi\files\program files\Advantage 12.0" -Destination "C:\Program Files (x86)"```


- Download modified versions.inc file:
    ```wget https://www.jd-engineering.de/wordpress/wp-content/uploads/2016/05/versions.inc_.txt -OutFile c:\adsdelphi\versions.inc```


- Make a copy of the latest supported Delphi version (my latest version isDelphi10SEATTLE):
    ```Copy-Item -Recurse -Path "C:\Program Files (x86)\Advantage 12.0\TDataset\Delphi10SEATTLE" -Destination "C:\Program Files (x86)\Advantage 12.0\TDataset\Delphi101Berlin"```


- Replace versions.inc files:

```copy -Confirm C:\adsdelphi\versions.inc "C:\Program Files (x86)\Advantage 12.0\TDataset\Delphi101Berlin\Win32\versions.inc"
copy -Confirm C:\adsdelphi\versions.inc "C:\Program Files (x86)\Advantage 12.0\TDataset\Delphi101Berlin\Win32\Source\versions.inc"
copy -Confirm C:\adsdelphi\versions.inc "C:\Program Files (x86)\Advantage 12.0\TDataset\Delphi101Berlin\Win64\versions.inc"
copy -Confirm C:\adsdelphi\versions.inc "C:\Program Files (x86)\Advantage 12.0\TDataset\Delphi101Berlin\Win64\Source\versions.inc"
```


- Search files:

```Get-ChildItem -Path "C:\Program Files (x86)\Advantage 12.0\" -Filter adsdxe8studio.dproj -Recurse```

