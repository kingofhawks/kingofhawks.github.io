There are many distributed file systems.

Some are AWS S3 compatible:

### Ceph

[Ceph](http://ceph.com/) with a REST interface that’s compatible with applications written for S3 and Swift, acquired by Redhat. Implement Object storage,block storage and file system.


### FakeS3
[FakeS3](https://github.com/jubos/fake-s3) is a lightweight server that responds to the same calls Amazon S3 responds to. It is extremely useful for testing of S3 in a sandbox environment without actually making calls to Amazon, which not only require network, but also cost you precious dollars.


### minio
[minio.io](http://minio.io/) is Go cloud storage compatible with S3



### OpenStack Swift


### eucalyptus


### Riak


### Gluster 


Others not:
### MongoDB GridFS
suitable for small files <=16M 


### HDFS 
Included in Apache Hadoop,rather complex and not suitable for small files


### TFS
Taobao File system


### seaweedfs
based on facebook haystack design paper


### Reference
[GridFS]https://dzone.com/articles/when-use-gridfs-mongodb
[Facebook Haystack]http://www.oenhan.com/haystack-tfs
[GFS](http://www.open-open.com/lib/view/open1328763454608.html)


