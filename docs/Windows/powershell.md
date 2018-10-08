# PowerShell

Internet Documents: <https://docs.microsoft.com/en-us/powershell/scripting/powershell-scripting?view=powershell-6>

## Basic

### list commands

`command` or `Get-Command`

`help`

`get-module`

`get-command -Module [module name]`

### help
  
`get-help [commad-name]` or `[command-name] -?`

ex: `get-help get-aduser` or `get-aduser -?`

### help full

`get-help [command-name] -full`

### get help about parameter for a command

`get-help [command-name] -Parameter [parameter/option name]`

### get help example

`get-help [command-name] -Examples`

## General

### Remote Powershell

`Enter-PSSession -ComputerName 192.168.60.5 -Credential risman`

## Windows Desktop

## Windows Server

### Active Directory

#### ETC

- CSV Directory Exchange > for export/import AD data to csv file

`csvde`

e.g:

`csvde -f ad-account-list.csv -d "ou=users,ou=Indonesia,ou=Voxteneo,dc=voxteneo,dc=internal" -r "(objectclass=user)"`

- ldif Directory Exchange > for export/import AD data to ldif file

`ldifde`

e.g:

`ldifde -f ad-account-list.ldif -d "ou=users,ou=Indonesia,ou=Voxteneo,dc=voxteneo,dc=internal" -r "(objectclass=user)"`

- Search Ad Acoount

`Search-ADAccount`

`get-help Search-ADAccount -full`

- how to create user from csv file

- DirectAccess Offline Domain Join

<https://docs.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/directaccess-offline-domain-join>

#### Get Data

list Command about Active Directory on powershell

`Get-Command -Module ActiveDirectory`

list Command about Active Directory filtered by "GET" on powershell

`Get-Command -Verb Get -Module ActiveDirectory`

getting help for filter paramater on Get-ADUser command

`Get-Help Get-ADUser –Parameter filter`

Getting AD data from remote AD server

`Get-ADUser -Server 192.168.60.5 -Filter * -SearchBase "OU=Voxteneo,OU=Indonesia,DC=voxteneo,DC=internal"`

`Get-ADUser -Server 192.168.60.5 -Filter * -SearchBase "OU=Indonesia,OU=Voxteneo,DC=voxteneo,DC=internal"  | sort | Format-Table Name, UserPrincipalName  -AutoSize`

`Get-ADUser -Server 192.168.60.5 -Filter * -SearchBase "OU=Indonesia,OU=Voxteneo,DC=voxteneo,DC=internal"  | Sort-Object -Property @{Expression = "Name"} | Format-Table Name,UserPrincipalName`

`Get-ADUser -Server 192.168.60.5 -Filter * -SearchBase "OU=Indonesia,OU=Voxteneo,DC=voxteneo,DC=internal"  | Sort-Object -Property @{Expression = "Name"; Descending = $True}, @{Expression = "UserPrincipalName"; Descending = $False} | Format-Table Name,UserPrincipalName`

<!-- Example -->

`Get-ADOrganizationalUnit -Server 192.168.60.5 -SearchBase "OU=Voxteneo,DC=voxteneo,DC=internal" -Filter * -Properties * | Get-Member`

`Get-ADOrganizationalUnit -Server 192.168.60.5 -SearchBase "OU=Voxteneo,DC=voxteneo,DC=internal" -Filter * -Properties CanonicalName | Select-Object CanonicalName`

`Get-ADOrganizationalUnit -Server 192.168.60.5 -SearchBase "OU=Voxteneo,DC=voxteneo,DC=internal" -Filter * -Properties DistinguishedName | Select-Object DistinguishedName`

`Get-ADObject -Server 192.168.60.5 -Filter { ObjectClass -eq 'organizationalunit' } | Sort-Object -Property @{Expression = "Name"} | Format-Table -AutoSize`

`help Get-ADUser`

To display the list of all domain accounts, run this command:

`Get-ADUser -filter *`

Important. It is not recommended to run this command in the domains with the large number of accounts, since the domain controller providing the information can be overloaded.

`Get-ADUser - get AD user data via Powershell

The format of the returned list isn’t too convenient, only some basic 10 of the more than 120 attributes and properties of user accounts (DN, SamAccountName, Name, SID, UPN, etc.) are displayed. We also see that the information about the time of the last password change is absent.

To display the detailed information about all available user attributes, run this command:

`Get-ADUser -identity tuser -properties *`

**get active directory user properties**

So we see the full list of AD attributes and their values associated with the user account. Then we’ll go to the formatting of Get-ADUser output so that the necessary fields are displayed. We are interested in the following properties:

- PasswordExpired
- PasswordLastSet
- PasswordNeverExpires

Run the command:

`Get-ADUser tuser -properties PasswordExpired, PasswordLastSet, PasswordNeverExpires`

or you can use `Search-ADaccount`

`get-help search-adaccount -full`

**get-aduser password info**

Now in the user data there is the information about the date of the last password change and the time of its expiration. Display this information in a more convenient table view:

`Get-ADUser -filter * -properties PasswordExpired, PasswordLastSet, PasswordNeverExpires | ft Name, PasswordExpired, PasswordLastSet, PasswordNeverExpires`

**get-aduser table view**

To display the data of the users from a certain OU, use SearchBase key:

`Get-ADUser -SearchBase ‘OU=London,DC=woshub,DC=loc’ -filter * -properties PasswordExpired, PasswordLastSet, PasswordNeverExpires | ft Name, PasswordExpired, PasswordLastSet, PasswordNeverExpires`

The result can be exported to a text file:

`Get-ADUser -filter * -properties PasswordExpired, PasswordLastSet, PasswordNeverExpires | ft Name, PasswordExpired, PasswordLastSet, PasswordNeverExpires > C:\temp\users.txt`

Also it can be exported to CSV file,  which is convenient to import to Excel. (also, using sort-object you can sort the table by PasswordLastSet column, and add the condition where — the user name has to contain the line “Dmitry”.).

`Get-ADUser -filter * -properties PasswordExpired, PasswordLastSet, PasswordNeverExpires | where {$_.name –like “*Dmitry*”} | sort-object PasswordLastSet | select-object Name, PasswordExpired, PasswordLastSet, PasswordNeverExpires | Export-csv -path c:\tmp\user-passwords-expires.csv`

**get-aduser sort**

So you can make a table with any attributes of Active Directory users.

To obtain data about Active Directory computers you need to use another cmdlet – Get-ADComputer.
To get a list of AD user accounts with a particular characteristic, use the -Filter parameter. As arguments of this parameter, you can specify the value of certain attributes of Active Directory users.

Let’s show some more useful options of Active Directory queries using different filters. You can combine them to perform a search to get multiple user AD objects.

Display AD users, whose name starts with Joe:

`Get-ADUser -filter {name -like "Joe*"}`

To calculate the total number of all Active directory accounts:

`Get-ADUser -Filter {SamAccountName -like "*"} | Measure-Object`

The list of all active (not blocked) AD accounts:

`Get-ADUser -Filter {Enabled -eq "True"} | Select-Object SamAccountName,Name,Surname,GivenName | Format-Table`

The list of the accounts with the expired password:

`Get-ADUser -filter {Enabled -eq $True} -properties passwordExpired | where {$_.PasswordExpired}`

The list of active accounts with e-mail addresses:

`Get-ADUser -Filter {(mail -ne "null") -and (Enabled -eq "true")} -Properties Surname,GivenName,mail | Select-Object Name,Surname,GivenName,mail | Format-Table`

Task: for the list of accounts that are stored in a text file (one account per line), you need to get the user’s company name from AD and save it to a text csv file (you can easily import this file into Excel).

`Import-Csv c:\ps\users_list.csv | ForEach {Get-ADUser -identity $_.user -Properties Name, Company | Select Name, Company |Export-CSV c:\ps\users_ad_list.csv -Append -Encoding UTF8}`

The next example allows to export the address book of the company to a CSV file, which can later be imported into email clients such as Outlook or Mozilla Thunderbird:

`Get-ADUser -Filter {(mail -ne "null") -and (Enabled -eq "true")} -Properties Surname,GivenName,mail | Select-Object Name,Surname,GivenName,mail | Export-Csv -NoTypeInformation -Encoding utf8 -delimiter "," $env:temp\adress_list.csv`

The users who haven’t changed their passwords in the last 90 days:

`$90_Days = (Get-Date).adddays(-90)`
`Get-ADUser -filter {(passwordlastset -le $90_days)}`

To get a user’s photo from Active Directory and save it to a file, run the following commands:
`$usr = Get-ADUser sjoe -Properties thumbnailPhoto`
`$usr.thumbnailPhoto | Set-Content sjoe.jpg -Encoding byte`

To get a list of AD groups which the user account is a member of:

`Get-AdUser sjoe -Properties memberof | Select memberof -expandproperty memberof`

#### Examples

`Get-ADUser -Filter * -SearchBase "OU=Voxteneo,DC=voxteneo,DC=internal" -Properties Name, SamAccountName, mail, whenCreated, whenChanged, PasswordLastSet, LastLogonDate | Sort-Object -Property @{Expression = "Name"} | ft Name, SamAccountName, mail, whenCreated, whenChanged, PasswordLastSet, LastLogonDate`

`Get-ADComputer -Filter * -SearchBase "DC=voxteneo,DC=internal"  -Properties Name, OperatingSystem, OperatingSystemVersion, whenCreated, whenChanged |Sort-Object -Property @{Expression = "OperatingSYstem"}| ft  Name, OperatingSystem, OperatingSystemVersion, whenCreated, whenChanged`