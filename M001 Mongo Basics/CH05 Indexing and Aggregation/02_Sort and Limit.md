## Sort 

### Ascending

    db.<collection_name>.find().sort( 
        { <field1>: 1, <field2>: 1, .. }
    )

### Descending

    db.<collection_name>.find().sort( 
        { <field1>: -1, <field2>: -1, ... }
    )

## Limit

    db.<collection_name>.find().limit(n)

## Quiz 2

### Problem

In what year was the youngest bike rider from the sample_training.trips collection born?

### Solution

    db.trips.find(

        { "birth year": { "$ne": "" } }, 
        { "birth year": 1 }
        
    ).sort({ "birth year": -1 }).limit(1)

### Result
    1999