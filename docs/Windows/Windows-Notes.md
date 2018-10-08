# Windows

## General

### Run mmc as another user

open powershell as admin and run this command

`runas /user:voxteneo\risman /netonly mmc.exe`

## Command on RUN

- gpmc.msc : Group Policy Management Console for Domain (AD)
- netplwiz : User Management
- gpedit.msc : Group Policy Edit (local)

| Windows Function                          | Run Command                                     |
| ----------------------------------------- | ----------------------------------------------- |
| Add Hardware Wizard                       | hdwwiz                                          |
| Adding a new Device                       | devicepairingwizard                             |
| Advanced User Accounts                    | azman.msc                                       |
| Advanced User Accounts                    | netplwiz                                        |
| Backup and Restore                        | sdclt                                           |
| Calculator                                | calc                                            |
| Certificates                              | certmgr.msc                                     |
| Character Map                             | charmap                                         |
| ClearType Tuner                           | cttune                                          |
| Color Management                          | colorcpl                                        |
| Command Prompt                            | cmd                                             |
| Component Services                        | comexp.msc                                      |
| Component Services                        | dcomcnfg                                        |
| Computer Management                       | compmgmt.msc                                    |
| Computer Management                       | compmgmtlauncher                                |
| Connect to a Projector                    | displayswitch                                   |
| Control Panel                             | control                                         |
| Credential Backup and Restore Wizard      | credwiz                                         |
| Data Execution Prevention                 | systempropertiesdataexecutionprevention         |
| Date and Time                             | timedate.cpl                                    |
| Device Manager                            | hdwwiz.cpl                                      |
| Diagnostics Troubleshooting Wizard        | msdt                                            |
| Digitizer Calibration Tool                | tabcal                                          |
| DirectX Diagnostic Tool                   | dxdiag                                          |
| Disk Cleanup                              | cleanmgr                                        |
| Disk Defragmenter                         | dfrgui                                          |
| Disk Management                           | diskmgmt.msc                                    |
| Display                                   | dpiscaling                                      |
| Display Color Calibration                 | dccw                                            |
| DPAPI Key Migration Wizard                | dpapimig                                        |
| Driver Verifier Manager                   | verifier                                        |
| Ease of Access Center                     | utilman                                         |
| Event Viewer                              | eventvwr.msc                                    |
| Fax Cover Page Editor                     | fxscover                                        |
| Game Controllers                          | joy.cpl                                         |
| Getting Started                           | irprops.cpl                                     |
| IExpress Wizard                           | iexpress                                        |
| Internet Explorer                         | iexplore                                        |
| Internet Options                          | inetcpl.cpl                                     |
| Language Pack Installer                   | lpksetup                                        |
| Local Users and Groups                    | lusrmgr.msc                                     |
| Magnifier                                 | magnify                                         |
| Malicious Software Removal Tool           | mrt                                             |
| Math Input Panel                          | mip                                             |
| Microsoft Management Console              | mmc                                             |
| Mouse                                     | main.cpl                                        |
| NAP Client Configuration                  | napclcfg.msc                                    |
| Narrator                                  | narrator                                        |
| Network Connections                       | ncpa.cpl                                        |
| New Scan Wizard                           | wiaacmgr                                        |
| Notepad                                   | notepad                                         |
| ODBC Data Source Administrator            | odbcad32                                        |
| On-Screen Keyboard                        | osk                                             |
| Open Documents Folder                     | documents                                       |
| Open Downloads Folder                     | downloads                                       |
| Open Favorites Folder                     | favorites                                       |
| Open Pictures Folder                      | pictures                                        |
| Open Recent Folder                        | recent                                          |
| Open Videos folder                        | videos                                          |
| Paint                                     | mspaint                                         |
| Pen and Touch                             | tabletpc.cpl                                    |
| People Near Me                            | collab.cpl                                      |
| Performance Monitor                       | perfmon.msc                                     |
| Performance Options                       | systempropertiesperformance                     |
| Phone and Modem                           | telephon.cpl                                    |
| Phone Dialer                              | dialer                                          |
| Power Options                             | powercfg.cpl                                    |
| Printer User Interface                    | printui                                         |
| Private Character Editor                  | eudcedit                                        |
| Problem Steps Recorder                    | psr                                             |
| Programs and Features                     | appwiz.cpl                                      |
| Region and Language                       | intl.cpl                                        |
| Registry Editor                           | regedit                                         |
| Remote Access Phonebook                   | rasphone                                        |
| Remote Desktop Connection                 | mstsc                                           |
| Resource Monitor                          | resmon                                          |
| SAM Lock Tool                             | syskey                                          |
| Screen Resolution                         | desk.cpl                                        |
| Services                                  | services.msc                                    |
| Set Program Access and Computer Defaults  | computerdefaults                                |
| Share Creation Wizard                     | shrpubw                                         |
| Shared Folder Wizard                      | shrpubw                                         |
| Shared Folders                            | fsmgmt.msc                                      |
| Snipping Tool                             | snippingtool                                    |
| Sound                                     | mmsys.cpl                                       |
| Sound recorder                            | soundrecorder                                   |
| SQL Server Client Network Utility         | cliconfg                                        |
| Sticky Notes                              | stikynot                                        |
| Sync Center                               | mobsync                                         |
| System Configuration                      | msconfig                                        |
| System Configuration Editor               | sysedit                                         |
| System Information                        | msinfo32                                        |
| System Properties                         | sysdm.cpl                                       |
| System Properties (Advanced Tab)          | systempropertiesadvanced                        |
| System Properties (Hardware Tab)          | systempropertieshardware                        |
| System Properties (Remote Tab)            | systempropertiesremote                          |
| System Properties (System Protection Tab) | systempropertiesprotection                      |
| System Restore                            | rstrui                                          |
| Task Manager                              | taskmgr                                         |
| Task Scheduler                            | taskschd.msc                                    |
| Taskbar and Start Menu                    | control.exe /name Microsoft.TaskbarandStartMenu |
| Troubleshooting                           | control.exe /name Microsoft.Troubleshooting     |
| Trusted Platform Module (TPM) Management  | tpm.msc                                         |
| User Account Control Settings             | useraccountcontrolsettings                      |
| User Accounts                             | control.exe /name Microsoft.UserAccounts        |
| Utility Manager                           | utilman                                         |
| Version Reporter Applet                   | winver                                          |
| Volume Mixer                              | sndvol                                          |
| Windows Action Center                     | wscui.cpl                                       |
| Windows Activation Client                 | slui                                            |
| Windows Anytime Upgrade                   | WindowsAnytimeUpgradeui                         |
| Windows Anytime Upgrade Results           | windowsanytimeupgraderesults                    |
| Windows Disc Image Burning Tool           | isoburn                                         |
| Windows DVD Maker                         | dvdmaker                                        |
| Windows Easy Transfer                     | migwiz                                          |
| Windows Explorer                          | explorer                                        |
| Windows Fax and Scan                      | wfs                                             |
| Windows Features                          | optionalfeatures                                |
| Windows Firewall                          | firewall.cpl                                    |
| Windows Journal                           | journal                                         |
| Windows Media Player                      | wmplayer                                        |
| Windows Memory Diagnostic Scheduler       | mdsched                                         |
| Windows Mobility Center                   | mblctr                                          |
| Windows PowerShell                        | powershell                                      |
| Windows PowerShell ISE                    | powershell_ise                                  |
| Windows Remote Assistance                 | msra                                            |
| Windows Repair Disc                       | recdisc                                         |
| Windows Script Host                       | wscript                                         |
| Windows Update                            | wuapp                                           |
| Windows Update Standalone Installer       | wusa                                            |
| WMI Management                            | wmimgmt.msc                                     |
| WordPad                                   | write                                           |
| XPS Viewer                                | xpsrchvw                                        |

## Active Directory

link to powershell documentation [PowerShell](powershell.md#active-directory)

### update group policy

run these commands on CMD

`gpupdate`

`gpupdate /force`

check group policy update status

`gpresult /r`
