## $expr Allows mongo compare field with value, field with field

## For Example

### Compare "end station id" field with "start station id" field

    db.trips.find(
        {
            "$expr": { "$eq": [ "$end station id", "$start station id" ] }
        }
    ).count()

### Combination Comparison: field with value, field with field
    db.trips.find(
        { 
            "$expr": { "$and": 
                        [ 
                            { "$gt": [ "$tripduration", 1200 ]},
                            { "$eq": [ "$end station id", "$start station id" ]}
                        ]
                      }
        }
    ).count()

## Lab

### Problem
How many companies in the sample_training.companies collection have the same permalink as their twitter_username?

### Solution
    db.companies.find(
        {
            "$expr": { "$eq": [ "$permalink", "$twitter_username" ] }
        }
    ).count()

### Result
    1299