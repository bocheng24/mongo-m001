## List all databases
    show dbs

## Switch to one db, and list all collections
    use <dbname> // it will create the db if not exists
    show collections

## List all documents in one collection
    db.<collection_name>.find()

## Filter out documents by condition
    db.<collection_name>.find({
        "field": "value",
        "field": "value",
        ...
    })

## Count a collection with or without fitler
    db.<collection_name>.find(<filter>).count()

## List the result pretty
    db.<collection_name>.find(<filter>).pretty()