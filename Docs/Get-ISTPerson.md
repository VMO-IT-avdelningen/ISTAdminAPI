Get-ISTPerson
===================

## SYNOPSIS
Retrieve one or more person(s) from IST.

## SYNTAX
```powershell
Get-ISTPerson [-NameContains <String>] [-ExpandProperties <String[]>] [<CommonParameters>]



Get-ISTPerson [-CivicNo <String>] [-ExpandProperties <String[]>] [<CommonParameters>]



Get-ISTPerson [-Id <String>] [-ExpandProperties <String[]>] [<CommonParameters>]



Get-ISTPerson [-RelationshipEntity <String>] [-RelationshipOrganisation <Guid>] [-ExpandProperties <String[]>] [-StartDateOnOrBefore <String>] [-StartDateOnOrAfter <String>] [-EndDateOnOrBefore <String>] [-EndDateOnOrAfter <String>] [<CommonParameters>]



Get-ISTPerson [-LookUp <String[]>] -LookUpType <String> [-ExpandProperties <String[]>] [<CommonParameters>]
```

## DESCRIPTION
With this cmdlet you will be able to retrieve persons from the EduCloud API based on what information you feed the different parameters with.

## PARAMETERS
### -NameContains &lt;String&gt;
Search filter. Based on the size of your organisation, this one might run slow.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -CivicNo &lt;String&gt;
Retrieve a person based on the civic number
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -Id &lt;String&gt;
Retrieve a person based on the Id
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -RelationshipEntity &lt;String&gt;
When used in conjunction with the "RelationshipOrganisation" parameter, this parameter will let you filter out persons that has a specific relationship to a specific organisation.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -RelationshipOrganisation &lt;Guid&gt;
Retrieve persons connected to one specific organsisation
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -LookUp &lt;String[]&gt;
Send an array of either ids or civic numbers to the API. When used, the "LookUpType" parameter becomes mandatory
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -LookUpType &lt;String&gt;
Specify what type of lookup you're doing. Either ids or civicnos
```
Required?                    true
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -ExpandProperties &lt;String[]&gt;
Allows you to expand specific properties when retrieving persons. Allows for multiple choices.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -StartDateOnOrBefore &lt;String&gt;
Only retrieve duties that starts on or before provided date. Must be RFC3339 format
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -StartDateOnOrAfter &lt;String&gt;
Only retrieve duties that starts on or before provided date
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -EndDateOnOrBefore &lt;String&gt;
Only retrieve duties that starts on or before provided date
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -EndDateOnOrAfter &lt;String&gt;
Only retrieve duties that starts on or before provided date
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
Author: Simon MellergÃ¥rd | It-center, VÃ¤rnamo kommun

## EXAMPLES
### EXAMPLE 1
```powershell
PS C:\>Get-ISTPerson -NameContains "Johan Johans" -ExpandProperties placements

# This example will search your organisation for persons that match the search filter "Johan Johans". Persons will be retrieved that match both words. E.g. persons named "Johan Johansson" and "Johan Johanson" will be returned. Returned persons placements will also be returned.
```

 
### EXAMPLE 2
```powershell
PS C:\>Get-ISTPerson -CivicNo 12345678xxxx -ExpandProperties duties, responsibleFor

# Here will spcify one specific persons civic number. We also say that we want that persons duties and the persons that are listed as having retrieved person as one of their responsibles.
```

 
### EXAMPLE 3
```powershell
PS C:\>Get-ISTPerson -Id 7ff9d599-ff4e-4eb8-baba-0d5a7f55752a -ExpandProperties groupMemberships

# In this example we specify one specific id to retrieve along with that persons group memberships.
```

 
### EXAMPLE 4
```powershell
PS C:\>Get-ISTPerson -RelationshipOrganisation fa971b78-d804-49b5-a736-ed7d62138727 -RelationshipEntity duty

# Here we retrieve all persons that has a duty at the specified organisation.
```

 
### EXAMPLE 5
```powershell
PS C:\>$Today = Get-Date -Format yyyy-MM-dd

Get-ISTPerson -RelationshipEntity duty -RelationshipOrganisation 2a00956d-18d9-41be-9621-b83ca92046ff -StartDateOnOrBefore $today -EndDateOnOrAfter $today
# Here we retrieve all persons that has a duty at the specified organisation that matches the start and end date filter provided.
```

 
### EXAMPLE 6
```powershell
PS C:\>$LookUpIds = @(

"55579f83-51ac-46fa-ad06-af6aa2a6d6be",
	"7b5995b7-c487-40c7-bcb6-b2ef81ff1b6d",
	"1862468d-b6d0-4fec-9147-df29c13ca847"
)
Get-ISTPerson -LookUp $LookUpIds -LookUpType ids -ExpandProperties duties, groupMemberships, responsibleFor, placements
# In this example we send 3 different ids to the API and specify that we want to expand duties, groupMemberships, responsibleFor and placements
```

 
### EXAMPLE 7
```powershell
PS C:\>$LookUpCivicNos = @(

"12345678xxxx",
	"87654321xxxx",
)
Get-ISTPerson -LookUp $LookUpCivicNos -LookUpType civicNos
# Here we send 2 different civic numbers to the API.
```


