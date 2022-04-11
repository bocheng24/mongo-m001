## Import BSON Data
mongorestore --uri <mongo_uri> --drop dump

## Import JSON Data
mongoimport --uri <mongo_uri> --drop=<output.json>