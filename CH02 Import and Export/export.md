## Mongo URI Format
    mongodb+srv://user:password/mongodb_server/dbname

## Export mongo data as BSON
    mongodump --uri <mongo_uri>

## Export mongo data as JSON
    mongoexport --uri <mongo_uri> --collection=<collection_name> --out=<output.json>
