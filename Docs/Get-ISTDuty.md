Get-ISTDuty
===================

## SYNOPSIS
Retrieve a duty from EduCloud

## SYNTAX
```powershell
Get-ISTDuty [-Organisation <Guid>] [-DutyRole <String>] [-PersonId <Guid>] [-ExpandPerson] [-StartDateOnOrBefore <String>] [-StartDateOnOrAfter <String>] [-EndDateOnOrBefore <String>] [-EndDateOnOrAfter <String>] [<CommonParameters>]



Get-ISTDuty [-Id <Guid>] [-ExpandPerson] [<CommonParameters>]



Get-ISTDuty [-LookUp <Guid[]>] [-ExpandPerson] [<CommonParameters>]
```

## DESCRIPTION
This cmdlet will help you retrieve one or more duties based on how you fill out the parameters.

## PARAMETERS
### -Organisation &lt;Guid&gt;
Retrieve duties connected to a specific organisation.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -DutyRole &lt;String&gt;
Only retrieve a specific type of duty
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -PersonId &lt;Guid&gt;
Retrieve all duties connected to a specific person
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -Id &lt;Guid&gt;
Retrieve a specific duty based on it's id.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -LookUp &lt;Guid[]&gt;
Feed this parameter with a hashtable of duty id's to retrieve them from the API
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -ExpandPerson &lt;SwitchParameter&gt;
Switch parameter that will provide the person connected to the duty/duties that you retrieve
```
Required?                    false
Position?                    named
Default value                False
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -StartDateOnOrBefore &lt;String&gt;
Must be in RFC3339 format - Will only retrieve duty/duties that either has the same starting date or started before
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -StartDateOnOrAfter &lt;String&gt;
Must be in RFC3339 format - Will only retrieve duty/duties that either has the same starting date or starts after
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -EndDateOnOrBefore &lt;String&gt;
Must be in RFC3339 format - Will only retrieve duty/duties that either has the same ending date or ends before
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -EndDateOnOrAfter &lt;String&gt;
Must be in RFC3339 format - Will only retrieve duty/duties that either has the same ending date or ends after
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```

## INPUTS


## OUTPUTS


## NOTES
Author: Simon Mellergård | It-center, Värnamo kommun

## EXAMPLES
### EXAMPLE 1
```powershell
PS C:\>$Today = Get-Date -Format yyyy-MM-dd

Get-ISTDuty -Organisation <Organisation GUID> -DutyRole Rektor -StartDateOnOrBefore $Today -EndDateOnOrAfter $Today
# This example will retrieve all duties with the duty role 'Rektor' that connected to the specified organisation. It will also filter out duties that don't match the provided start/end dates.
```

 
### EXAMPLE 2
```powershell
Get-ISTDuty -PersonId <Person GUID>

# This example will retrieve all duties connected to the specified person
```

 
### EXAMPLE 3
```powershell
PS C:\>$DutyIds = @(

"108f0e66-dadf-47b3-8c96-9122eebd141c",
	"dd181c39-c6c9-4d42-b2d7-86b66dcb6ad7",
	"f876453d-591f-4460-bd81-cd8b7a30a140",
	"1ad3aa60-b13d-4b5e-9dc5-e1f9c2deb9e0"
)

Get-ISTDuty -LookUp $DutyIds -ExpandPerson
# This example will retrieve all four duties declared in $DutyIds and also get the connected person as an expandable object.
```

 
### EXAMPLE 4
```powershell
PS C:\>Get-ISTDuty -DutyRole 'Studie- och yrkesvägledare'

# This example will retrieve all duties with the role 'Studie- och yrkesvägledare' from your entire organisation.
```


