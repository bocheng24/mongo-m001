## Insert document basic step

1. Connect to the mongo server
2. Switch to the database
3. perform insert

## Perform Insert

### A. Insert one document
    db.<collection_name>.insert( {JSON} )

### B. Insert multiple documents
    db.<collection_name>.insert( [{JSON}, {JSON}, ...] )

### C. If the data list has duplicated _id data, use {"ordered": false} to insert multiple documents to insert 
    b.<collection_name>.insert( 
        [{JSON}, {JSON}, ...],
        {"ordered": false}
    )

### C. Mongo will auto create <collection_name> if not exists

## The value of _id

* It is automatically generated as an <strong>ObjectId</strong> type value.
* You can select a non ObjectId type value when inserting a new document, as long as that value is <strong>unique</strong> to this collection.
* If a document is inserted without a provided _id value, then the _id field and value will be automatically generated for the inserted document before insertion.
* MongoDB can store duplicate documents in the same collection, as long as their _id values are different.