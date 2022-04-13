## Upsert

### Update or Insert

## How does the upsert option work?
* By default upsert is set to false.

* When upsert is set to true and the query predicate returns an empty cursor, the update operation creates a new document using the directive from the query predicate and the update predicate.

* When upsert is set to false and the query predicate returns an empty cursor then there will be no updated documents as a result of this operation.

### Syntax

    db.<collection_name>.updateMany(
        { <Filter_condition> },
        { <Update_operator> },
        { "upsert": true }
    )


### Be mind, make sure that the update operator is enough to create a new document before enabling upsert