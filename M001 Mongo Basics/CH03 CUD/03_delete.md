## Delete Records

### Delete many

    db.<collection_name>.deleteMany( { Filter_condition } )

### Delete one

    db.<collection_name>.deleteOne( { Filter_condition } )

### For Example

###
    db.inspections.deleteOne({ "test": 3 })

###
    db.inspections.deleteMany({ "test": 1 })