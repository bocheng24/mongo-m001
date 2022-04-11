## Insert document basic step

1. Connect to the mongo server
2. Switch to the database
3. perform insert

#
    db.<collection_name>.insert( {JSON} )

## The value of _id

* It is automatically generated as an <strong>ObjectId</strong> type value.
* You can select a non ObjectId type value when inserting a new document, as long as that value is <strong>unique</strong> to this collection.