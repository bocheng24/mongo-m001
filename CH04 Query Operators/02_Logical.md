## Four Logical Operators

* $and - Returns all documents that match the conditions of both clauses.
* $or - Returns all documents that match the conditions of either clause.
* $nor - Returns all documents that fail to match both clauses.
* $not - Inverts the effect of a query expression and returns documents that do not match the query expression.

## Logical Syntax

### Array Syntax 
Apples to $and, $or, $nor

    db.<collection_name>.find(
        {
            <operator>: [{<field1>: <value1>}, {<field2>: <value2>}]
        }
    )

### Non Array Syntax
Applies to $not

    db.<collection_name>.find(
        {
            "$not": {<field1>: <value1>}
        }
    )

## For Example

    db.routes.find(
        {
            "$or": [
                    { "dst_airport": "KZN" },
                    { "src_airport": "KZN" }
                   ]
        }
    ).pretty()

###
    db.routes.find(
        {
            "$nor": [
                    { "dst_airport": "KZN" },
                    { "src_airport": "KZN" }
                   ]
        }
    ).pretty()

#### Combining with comparison operator
    db.trips.find(
        {
            "$or": [
                {"birth year": { "$lt": 1980 }},
                {"birth year": { "$gt": 2000 }}
            ]
        }
    ).pretty()

## Quiz 1
### Problem
How many businesses in the sample_training.inspections dataset have the inspection result "Out of Business" and belong to the "Home Improvement Contractor - 100" sector?

### Solution
    db.inspections.find(
        {
            "result": "Out of Business",
            "sector": "Home Improvement Contractor - 100"
        }
    ).count()

### Result
    4

    