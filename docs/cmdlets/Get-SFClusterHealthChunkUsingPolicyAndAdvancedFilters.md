# Get-SFClusterHealthChunkUsingPolicyAndAdvancedFilters
Gets the health of a Service Fabric cluster using health chunks.
## Description

Gets the health of a Service Fabric cluster using health chunks. The health evaluation is done based on the input 
cluster health chunk query description.
                The query description allows users to specify health policies for evaluating the cluster and its 
children.
                Users can specify very flexible filters to select which cluster entities to return. The selection can 
be done based on the entities health state and based on the hierarchy.
                The query can return multi-level children of the entities based on the specified filters. For example, 
it can return one application with a specified name, and for this application, return
                only services that are in Error or Warning, and all partitions and replicas for one of these services.



## Optional Parameters
#### -NodeFilters

Defines a list of filters that specify which nodes to be included in the returned cluster health chunk.
                    If no filters are specified, no nodes are returned. All the nodes are used to evaluate the 
cluster's aggregated health state, regardless of the input filters.
                    The cluster health chunk query may specify multiple node filters.
                    For example, it can specify a filter to return all nodes with health state Error and another 
filter to always include a node identified by its NodeName.



#### -ApplicationFilters

Defines a list of filters that specify which applications to be included in the returned cluster health chunk.
                    If no filters are specified, no applications are returned. All the applications are used to 
evaluate the cluster's aggregated health state, regardless of the input filters.
                    The cluster health chunk query may specify multiple application filters.
                    For example, it can specify a filter to return all applications with health state Error and 
another filter to always include applications of a specified application type.



#### -ConsiderWarningAsError

Indicates whether warnings are treated with the same severity as errors.



#### -MaxPercentUnhealthyNodes

The maximum allowed percentage of unhealthy nodes before reporting an error. For example, to allow 10% of nodes to be 
unhealthy, this value would be 10.
                    
                    The percentage represents the maximum tolerated percentage of nodes that can be unhealthy before 
the cluster is considered in error.
                    If the percentage is respected but there is at least one unhealthy node, the health is evaluated 
as Warning.
                    The percentage is calculated by dividing the number of unhealthy nodes over the total number of 
nodes in the cluster.
                    The computation rounds up to tolerate one failure on small numbers of nodes. Default percentage is 
zero.
                    
                    In large clusters, some nodes will always be down or out for repairs, so this percentage should be 
configured to tolerate that.



#### -MaxPercentUnhealthyApplications

The maximum allowed percentage of unhealthy applications before reporting an error. For example, to allow 10% of 
applications to be unhealthy, this value would be 10.
                    
                    The percentage represents the maximum tolerated percentage of applications that can be unhealthy 
before the cluster is considered in error.
                    If the percentage is respected but there is at least one unhealthy application, the health is 
evaluated as Warning.
                    This is calculated by dividing the number of unhealthy applications over the total number of 
application instances in the cluster, excluding applications of application types that are included in the 
ApplicationTypeHealthPolicyMap.
                    The computation rounds up to tolerate one failure on small numbers of applications. Default 
percentage is zero.



#### -ApplicationTypeHealthPolicyMap

Defines a map with max percentage unhealthy applications for specific application types.
                    Each entry specifies as key the application type name and as value an integer that represents the 
MaxPercentUnhealthyApplications percentage used to evaluate the applications of the specified application type.
                    
                    The application type health policy map can be used during cluster health evaluation to describe 
special application types.
                    The application types included in the map are evaluated against the percentage specified in the 
map, and not with the global MaxPercentUnhealthyApplications defined in the cluster health policy.
                    The applications of application types specified in the map are not counted against the global pool 
of applications.
                    For example, if some applications of a type are critical, the cluster administrator can add an 
entry to the map for that application type
                    and assign it a value of 0% (that is, do not tolerate any failures).
                    All other applications can be evaluated with MaxPercentUnhealthyApplications set to 20% to 
tolerate some failures out of the thousands of application instances.
                    The application type health policy map is used only if the cluster manifest enables application 
type health evaluation using the configuration entry for HealthManager/EnableApplicationTypeHealthEvaluation.



#### -ApplicationHealthPolicyMap

The wrapper that contains the map with application health policies used to evaluate specific applications in the 
cluster.



#### -ServerTimeout

The server timeout for performing the operation in seconds. This timeout specifies the time duration that the client 
is willing to wait for the requested operation to complete. The default value for this parameter is 60 seconds.



