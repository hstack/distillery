*"Amazon Kinesis is a fully managed service for real-time processing of streaming data at massive scale."*

I'd say that is rather a fully-managed distributed queuing service (something better than SQS) because you need to deploy and manage and pay the consumer applications separately, yourself. [[more](http://docs.aws.amazon.com/kinesis/latest/dev/step-four-operate-the-app.html)].  

In OSS parlance Kinesis would be similar to Kafka. The managed part would be the Kafka brokers.


### Highlights:

* Typical (advertised) lantecy is in the seconds range
* Data persistence is 24 hours
* Built-in fault tolerance
* Synchronous replication across multiple Availability Zones in a Region
* "at least once" semantics


### Concepts
Producers, Streams, Shards, Partition Keys, Sequence Numbers, Applications (processors/consumers)
![Architecture][http://docs.aws.amazon.com/kinesis/latest/dev/images/architecture.png]

An Amazon Kinesis **stream** is composed of multiple **shards**.  

You can **dynamically resize** your Amazon Kinesis stream or **add and remove shards** after the stream has been
created and while it has a Kinesis application running that is consuming data from the stream.


### Pricing

* \$0.015 / shard / hour (max 1 MBps ingress, 2 MBps egress)
* \$0.028 per 1M put transactions

### Sizes and limits

Multiple  different Kinesis applications can read from a shard.  

Each shard can support:

**Read**

* up to 5 read transactions per second 
* up to a maximum total of 2 MB of data read per second. 

**Write**

* up to 1000 write transactions per second 
* up to a maximum total of 1 MB data written per second. 

**Sizes**

* 50 kilobytes (KB) blob per PUT

**Persistence**

* Data records are accessible for only 24 hours from the time that they are added to an Amazon Kinesis stream.

**Other**

* CreateStream, ListStreams, DeleteStream, MergeShards, SplitShard operations — 5 transactions per second per account.
* DescribeStream — 10 transactions per second per account.
 


### Availability
Amazon Kinesis is available in the US East (Northern Virginia) region.	 	 

### Reference
[1] - [Product Details](http://aws.amazon.com/kinesis/details/)  
[2] - [Key Concepts](http://docs.aws.amazon.com/kinesis/latest/dev/key-concepts.html)  
[3] - [Processor](http://docs.aws.amazon.com/kinesis/latest/dev/kinesis-record-processor-app.html)  
[4] - [Operations](http://docs.aws.amazon.com/kinesis/latest/dev/step-four-operate-the-app.html)  
[5] - [API Refecence](http://docs.aws.amazon.com/kinesis/latest/APIReference/API_Operations.html)  
[6] - [Pricing](http://aws.amazon.com/kinesis/pricing/)
