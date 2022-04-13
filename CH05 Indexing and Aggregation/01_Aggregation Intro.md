## Using the aggregation framework find all documents that have Wifi as one of the amenities``*.

    db.listingsAndReviews.aggregate (
        [
            { "$match": { "amenities": "Wifi" } },
            { "$project": { 
                    "price": 1,
                    "address": 1,
                    "_id": 0 
                }
            }
        ]
    ).pretty()

## Group all documents into one document per address.country and amenities value.
    db.listingsAndReviews.aggregate (
        [ 
            { "$project": { 
                "address": 1, 
                "amenities": 1, 
                "_id": 0 }
            },
            { "$group": { "_id": [ "$address.country", "$amenities" ]}}
        ]
    ).pretty()

## Group by address.country and count country

    db.listingsAndReviews.aggregate (
        [
            { "$project": { "address": 1, "_id": 0 } },
            { "$group": { 
                    "_id": "$address.country",
                    "count": { "$sum": 1 } 
                } 
            }
        ]
    )

## Lab

### Problem

What room types are present in the sample_airbnb.listingsAndReviews collection?

### Solution
    db.listingsAndReviews.aggregate (
        
        { "$project": { "room_type": 1, "_id": 0 } },
        { "$group": {
                "_id": "$room_type"
            } 
        }
    )

### Result
    Private room
    Entire home/apt
    Shared room"