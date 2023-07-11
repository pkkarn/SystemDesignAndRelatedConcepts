# Acid Compliances

ACID compliance refers to a set of properties that guarantee reliable processing of `database transactions`. ACID is an acronym that stands for:

1. `Atomicity`: This property ensures that a transaction is treated as a single, indivisible unit of work, which means that all parts of the transaction are completed successfully, or none of them are. If a single part of the transaction fails, the entire transaction fails, and any changes are rolled back (undone).

```
Atomicity: Atomicity ensures that both these operations (subtracting from savings and adding to checking) happen completely or not at all. Let's say the $500 was deducted from the savings account, but due to some error, it could not be added to the checking account. In a system following atomicity, the entire transaction would fail and the $500 would be added back to the savings account. The system treats the entire transaction as a single, indivisible unit.
```

2. `Consistency`: This property ensures that a transaction brings a database from one valid state to another. The database must satisfy a set of defined rules, or integrity constraints, before and after the transaction. If a transaction would violate these constraints, it's rolled back.



Example: 
```
Consistency: Consistency ensures that the transaction brings the database from one valid state to another. Before the transaction, the total money in both accounts was a certain amount. After transferring $500, the total should remain the same, only distributed differently. If not, for example, if $500 was subtracted from the savings but $600 was added to the checking, it would violate consistency rules, and the transaction would be rolled back.
```

```
Consistency is like saying: If I start with 10 apples in each basket (20 in total), and I move 5 apples from the first basket to the second, then I should end up with 5 apples in the first basket and 15 in the second, but still 20 in total.

If somehow I end up with 6 apples in the first basket and 15 in the second (21 in total), something has gone wrong, because the total number of apples has increased. This shouldn't happen because we are just moving apples, not creating new ones.

So, consistency in database transactions means that all the data should follow certain rules before and after the transaction. If any rule is broken (like the total number of apples changing in our example), the transaction should be stopped and reversed.
```

3. `Isolation`: This property ensures that concurrent transactions occur as if they were executed sequentially, preventing them from interfering with each other. If two transactions are running concurrently, the results must be the same as if they were executed one after the other.

Example: 

```
Isolation: Let's say at the same time as the transfer, another transaction is trying to withdraw $200 from the savings account. Isolation ensures these transactions don't interfere with each other. The transactions should be scheduled in such a way (even if they're executed concurrently) that their outcome is the same as if they had been executed one after another.
```

4. `Durability`: This property ensures that once a transaction is committed, its effects are permanent and survive future system and software failures. This is usually achieved by storing the transaction details in a log that can be replayed in the event of a system failure.

Example: 

```
Durability: Once the $500 has been successfully transferred, the change should be permanent. Even if the system crashes right after the transaction, when it recovers, the changes should persist. This is usually achieved by storing all transaction information in a durable log, so that even in the case of a system failure, the system can return to the correct state.
```

## UseCases

To insure `isolation`:

```
In an application where two people hit the request at the same time, each request would create a new session and start a new transaction.

For example, if both requests are attempting to withdraw money from the same account, each request would independently check if there is enough money in the account and then try to perform the withdrawal. Here's where MongoDB's concurrency control and isolation come into play.

When one transaction is in progress (i.e., it has started but not yet committed), the changes it makes are not visible to other transactions. So if two withdrawal transactions start at roughly the same time, each will see the original balance in the account (because they can't see each other's changes).

Once a transaction is committed, its changes become visible to other transactions. If the first transaction commits successfully, it will decrease the balance. When the second transaction tries to commit, if the new balance (after the first transaction) is too low to allow the withdrawal, the second transaction will fail when it checks the account balance, thus preserving the integrity of the account balance.

So in this way, even when multiple clients are making requests at the same time, the integrity of the data in the database is preserved.
```

## Mongoose example to maintain and follow ACID (Atmocity and consistency part)

```js
const session = client.startSession();
session.startTransaction();

try {
    const accountsCollection = client.db("myDB").collection("accounts");

    // subtract $500 from savings
    await accountsCollection.updateOne(
        { accountType: "savings" },
        { $inc: { balance: -500 } },
        { session }
    );

    // add $500 to checking
    await accountsCollection.updateOne(
        { accountType: "checking" },
        { $inc: { balance: 500 } },
        { session }
    );

    await session.commitTransaction();
} catch (error) {
    console.error("Transaction aborted due to error: ", error);
    await session.abortTransaction();
} finally {
    session.endSession();
}
```

In the above example, we're enforcing consistency by ensuring that the total balance across the two accounts remains the same before and after the transaction. If either of the update operations fail (e.g., because the savings account doesn't have enough balance), the entire transaction is aborted, ensuring that the state of the database remains consistent.

## The Cap Theroem

CAP Theorem, also known as Brewer's theorem, is a concept that a distributed computing system is not able to provide all of the following three guarantees simultaneously:

- `Consistency`: All nodes see the same data at the same time. In other words, a query to the system returns the latest update across all nodes.

- `Availability`: Every request gets a response, without guarantee that it contains the most recent update. In other words, all nodes are always accessible for queries and updates.

- `Partition Tolerance`: The system continues to function despite arbitrary message loss or network failure – it can handle network failures between nodes.

The CAP Theorem states that in the presence of a network partition (when communication between nodes breaks down), one has to choose between consistency and availability.

For example, if we have a distributed database and a network failure occurs between two data centers, we have two options:

Stop all operations until the network issue is fixed, maintaining consistency but losing availability.
Continue with operations and sync the data after the network is fixed, maintaining availability but potentially losing consistency.
Different databases make different trade-offs based on the CAP theorem:

Traditional SQL databases like PostgreSQL and MySQL prioritize consistency (ACID properties) over availability.
Some NoSQL databases like Cassandra or Riak prioritize availability over consistency.
Some databases like MongoDB try to balance between the two based on the use case. However, with MongoDB, there is also an option to configure read and write options to favor either consistency or availability, depending on specific application needs