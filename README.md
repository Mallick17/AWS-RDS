Q: How does the storage auto scaling in rds happens or how does the size of the rds increases?

<details>
  <summary>Click to view Answer</summary>

- You can't reduce the amount of storage for a DB instance after storage has been allocated. When you increase the allocated storage, it must be by at least 10 percent. If you try to increase the value by less than 10 percent, you get an error. Scaling storage for RDS for SQL Server DB instances is supported only for the General Purpose SSD and Provisioned IOPS SSD storage types. [Increasing DB instance storage capacity](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.ModifyingExisting.html)
- You must set the maximum storage threshold to at least 10% more than the current allocated storage. We recommend setting it to at least 26% more to avoid receiving an event notification that the storage size is approaching the maximum storage threshold.
- For example, if you have DB instance with 1000 GiB of allocated storage, then set the maximum storage threshold to at least 1100 GiB. If you don't, you get an error such as Invalid max storage size for engine_name. However, we recommend that you set the maximum storage threshold to at least 1260 GiB to avoid the event notification. [Managing capacity automatically with Amazon RDS storage autoscaling](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.Autoscaling.html)
- Storage optimization can take several hours. You can't make further storage modifications for either six (6) hours or until storage optimization has completed on the instance, whichever is longer. 

</details>
