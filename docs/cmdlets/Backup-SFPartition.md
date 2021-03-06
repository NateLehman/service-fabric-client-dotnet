# Backup-SFPartition
Triggers backup of the partition's state.
## Description

Creates a backup of the stateful persisted partition's state. In case the partition is already being periodically 
backed up, then by default the new backup is created at the same backup storage. One can also override the same by 
specifying the backup storage details as part of the request body. Once the backup is initiated, its progress can be 
tracked using the GetBackupProgress operation. 
                In case, the operation times out, specify a greater backup timeout value in the query parameter.



## Required Parameters
#### -PartitionId

The identity of the partition.



#### -ConnectionString

The connection string to connect to the Azure blob store.



#### -ContainerName

The name of the container in the blob store to store and enumerate backups from.



#### -Path

UNC path of the file share where to store or enumerate backups from.



## Optional Parameters
#### -FriendlyName

Friendly name for this backup storage.



#### -PrimaryUserName

Primary user name to access the file share.



#### -PrimaryPassword

Primary password to access the share location.



#### -SecondaryUserName

Secondary user name to access the file share.



#### -SecondaryPassword

Secondary password to access the share location



#### -BackupTimeout

Specifies the maximum amount of time, in minutes, to wait for the backup operation to complete. Post that, the 
operation completes with timeout error. However, in certain corner cases it could be that though the operation returns 
back timeout, the backup actually goes through. In case of timeout error, its recommended to invoke this operation 
again with a greater timeout value. The default value for the same is 10 minutes.



#### -ServerTimeout

The server timeout for performing the operation in seconds. This timeout specifies the time duration that the client 
is willing to wait for the requested operation to complete. The default value for this parameter is 60 seconds.



