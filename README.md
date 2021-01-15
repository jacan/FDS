
# Datamodel and Pseudo code proposal for FDS
 ### Author: 	Jack Andersen
### State: 	Proposal
### Version: 	0.1

## DATAMODEL #

- **Update Request**
Represents a request based on PackageId and Clients current application version. 
If a specific version is present (not required) then the API will attempt to get updates within the requested version.

- **Update Response**
Descriptor returned with metadata about requested update for an application Package. 
The Response contains none or a range of software update packages. 

- **ReleaseChannel**
Describes a release channel fx Insider, Beta, Public, Interal etc

- **GeoLocation**
Describes a specifc geographic location and can include a region

- **PackageDefinition**
Represents a Software Package with information about name, release channel, and possible and 
geographic availability. 

- **Package** 
Represents a specific software package availbale for download based on a package definition. 
Contains its version and if any dependencies a dependant version.



## PSEUDO CODE PROPOSED FOR INTERACTING WITH FDS #


### Api Action

    enter code here

    var package = Get Package Based on CurrentVersion
    var version = get newest package version
    
    if SpecificVersion and is greater than CurrentVersion
    	verion = get specificversion
    	
    var updatePackagesForClient = Where 
    	Versions greater than CurrentVersion and less or equal to version 
    	and Is Available In Region 
    	and Channel matches definition
    		
    
    var responseForClient = set metadata for update response
    responseForClient add updatePackagesForClient
    
    return responseForClient 

### Client Update Action

    var package = application package id
    var version = application version
    
    var response = get available updates from API based on package and version
    
    for each update by version in order 
    	var binaryupdate = get binary from update.PackageUrl
    	execute binaryupdate
    	verify update
    	
    	
    end update loop


