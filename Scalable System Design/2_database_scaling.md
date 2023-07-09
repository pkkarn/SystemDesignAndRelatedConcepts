## Scaling Database

> Failover Strategy for Vertical Database

#### 1. Cold Standby

One way to overcome this by taking periodic backup, and in this way if that database goes down you can take old one and replace that with it.

**Disadvantages**

- Because its periodic thats why you will not have data after last backup.
- it can take a long time to replace that

#### 2. Warm Standby

In this case, instead of periodic backup, your data is being directly replicated to other database at standby as well. So, you will not have any `data-loss` thing. You can simulatneously write data at the same time.


**Disadvantages**

- Still it's a same vertical scaling because we have just another giant database ready to take place,
in case if something goes bad. but if it's still depends and limited to how much that database can handle.

#### 3. Hot Standby

In this case, instead of just replication done by server, client simultaneously store data in all other
database instance at the same time. 

## Horizontal Scaling of Database

Here you have request router in between that would have to pickup one of the shards. A shard is basically
partition of your database. Here you can keep adding shards as you need. Each shard will have their own
`backup` shard, which will take place in case if that shard goes down

So, here router will be sending one subset of data to one shard and another to different one...

**Advantages**:

- Even in any scenario if one shard goes down, then all the other would be still alive, its not a single
point of failure. 

- And because of each shard has it own backup shard, so in case if one shard goes down then other one would take place.

**Disadvantages**:

- It adds complexity, as you can imagine because your data are stored in different shards... So in case
if you want to perform join operations from these two shards, then it becomes complex thing. 