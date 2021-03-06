# Copy-SFServicePackageToNode
Downloads all of the code packages associated with specified service manifest on the specified node.
## Description

This API provides a way to download code packages including the container images on a specific node outside of the 
normal application deployment and upgrade path. This is useful for the large code packages and container images to be 
present on the node before the actual application deployment and upgrade, thus significantly reducing the total time 
required for the deployment or upgrade.



## Required Parameters
#### -NodeName

The name of the node.



#### -ServiceManifestName

The name of service manifest whose packages need to be downloaded.



#### -ApplicationTypeName

The application type name as defined in the application manifest.



#### -ApplicationTypeVersion

The version of the application type as defined in the application manifest.



#### -NodeName

The name of a Service Fabric node.



## Optional Parameters
#### -PackageSharingPolicy

List of package sharing policy information.



#### -ServerTimeout

The server timeout for performing the operation in seconds. This timeout specifies the time duration that the client 
is willing to wait for the requested operation to complete. The default value for this parameter is 60 seconds.



