Get-ISTOrganisation
===================

## SYNOPSIS
Retrieve an organisation

## SYNTAX
```powershell
Get-ISTOrganisation [-OrgType <String[]>] [-SchoolType <String[]>] [-Parent <Guid[]>] [<CommonParameters>]



Get-ISTOrganisation [-Id <Guid>] [<CommonParameters>]



Get-ISTOrganisation [-LookUp_Ids <Guid[]>] [-LookUp_SchoolUnitCodes <String[]>] [-LookUp_OrganisationCodes <String[]>] [<CommonParameters>]
```

## DESCRIPTION
With this cmdlet you will be able to retrieve your organisations in a couple of different ways.

## PARAMETERS
### -OrgType &lt;String[]&gt;
Retrieve organisations based on what type of organisation it is. Accepts values from a predefined list of strings. It's possible to feed the parameter with more than one value.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -SchoolType &lt;String[]&gt;
Retrieve organisations based on what type of school it is. Accepts values from a predefined list of strings. It's possible to feed the parameter with more than one value.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -Id &lt;Guid&gt;
Retrieve one specific organisation based on it's id.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -Parent &lt;Guid[]&gt;
Retrieve organisations connected to provided id. It is possible to feed the parameter with multiple values.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -LookUp_Ids &lt;Guid[]&gt;
With this parameter will let you send an object to the API containing multiple ids of organisations that you want to retrieve.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByValue)
Accept wildcard characters?  false
```
 
### -LookUp_SchoolUnitCodes &lt;String[]&gt;
With this parameter will let you send an object to the API containing multiple schoolUnitCodes of organisations that you want to retrieve.
```
Required?                    false
Position?                    named
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```
 
### -LookUp_OrganisationCodes &lt;String[]&gt;
With this parameter will let you send an object to the API containing multiple organisationCodes of organisations that you want to retrieve.
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
PS C:\>Get-ISTOrganisation -OrgType Huvudman

# In this example you will retrieve your principal organisation.
```

 
### EXAMPLE 2
```powershell
PS C:\>Get-ISTOrganisation -SchoolType GY

# This example will retrieve all organisations with the schoolType GY.
```

 
### EXAMPLE 3
```powershell
PS C:\>Get-ISTOrganisation -Id "24445547-9278-4c5a-ac0d-78cc6bf487a3"

# Retrieve one specific organisation.
```

 
### EXAMPLE 4
```powershell
PS C:\>Get-ISTOrganisation -Parent "874a3d02-25ff-4a32-b1d3-f03583f6e071"

# Retrieve all organisations that has provided id as their parent organisation.
```

 
### EXAMPLE 5
```powershell
PS C:\>Get-ISTOrganisation -Parent @("e95350b8-e162-41bd-b914-e162733f15e1", "71d2f3e2-ad74-4c22-81cc-c43eccd91dfc")

# Retrieve organisations from multiple parent organisations.
```

 
### EXAMPLE 6
```powershell
PS C:\>Get-ISTOrganisation -LookUp_Ids @("071546fb-5d2b-4905-b29a-fd2f46ea0c51", "bfd49638-c7e5-465c-8658-f6eaf0aa380f")

# Send one post to the API containing multiple ids to retrieve.
```


