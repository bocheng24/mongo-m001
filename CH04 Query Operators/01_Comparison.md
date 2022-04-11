## Basic comparison operators

* $eq: =
* $ne: != or <>
* $gt: >
* $lt: <
* $gte: >=
* $lte: <=

## Filter syntax

    db.<collection_name>.filter(
        {
            <field>: { <opearator>: <value> }
        }
    )

### For Example

    db.trips.find(
        { 
            "tripduration": { "$lte" : 70 },
            "usertype": { "$ne": "Subscriber" } 
        }
    ).pretty()

###
    db.trips.find(
        {
            "tripduration": { "$lte" : 70 },
            "usertype": { "$eq": "Customer" }
        }
    ).pretty()

###
    db.trips.find(
        { 
            "tripduration": { "$lte" : 70 },
            "usertype": "Customer" 
        }
    ).pretty()

## Lab 1

#### Problem

How many documents in the sample_training.zips collection have fewer than 1000 people listed in the pop field?

#### Solution

    db.zips.find(
        {
            "pop": { "$lt": 1000 }
        }
    ).count()

#### Result 
    8065

## Lab 2

#### Problem

What is the difference between the number of people born in 1998 and the number of people born after 1998 in the sample_training.trips collection?

#### Solution

    db.trips.find(
        {"birth year": {"$eq": 1998}}
    ).count() - 
    db.trips.find(
        {"birth year": {"$gt": 1998}}
    ).count()

#### Result 
    6