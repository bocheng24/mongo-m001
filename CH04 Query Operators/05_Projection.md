## Projection 
### The way to select specific fields to be or not to be displayed

## Projection Syntax

### To display certain fields
    db.<collection_name>.find(
        { <query conditions> },
        { <field_1>: 1, <field_2>: 1, ... }
    )

### To exclude some fields
    db.<collection_name>.find(
        { <query conditions> },
        { <field_1>: 0, <field_2>: 0, ... }
    )

## To query sub elements
### Like query "type" in "scores" field

    {
        "_id" : ObjectId("56d5f7eb604eb380b0d8d8cf"),
        "student_id" : 0,
        "scores" : [
            {
                "type" : "exam",
                "score" : 91.97520018439039
            },
            {
                "type" : "quiz",
                "score" : 95.80410375967175
            },
        ],
        "class_id" : 350
    }

### Syntax

    db.<collection_name>.find(
        {
            <parent_field>: {
                "$elemMatch": { <sub_field>: <value> }
            }
        }
    )

###
    db.grades.find(
        { "class_id": 431 },
        { 
            "scores": { 
                "$elemMatch": { "score": { "$gt": 85 } } 
            }
        }
    ).pretty()

## Lab

### Problem
How many companies in the sample_training.companies collection have offices in the city of Seattle?

### Solution
    db.companies.find(
        {
            "offices": {
                "$elemMatch": { "city": "Seattle" }
            }
        }
    ).count()

### Result
    117