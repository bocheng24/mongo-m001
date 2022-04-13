## Update Records

### Update many

    db.<collection_name>.updateMany(
        { Filter_Condition },
        {
            <operator1>: {<field1>: <new_value>, <field2>: <new_value>, ...},
            <operator2>: {<field1>: <new_value>, <field2>: <new_value>, ...},
            ...
        }
    )

### Update One

    db.<collection_name>.updateMany(
        { Filter_Condition },
        {
            <operator1>: {<field1>: <new_value>, <field2>: <new_value>, ...},
            <operator2>: {<field1>: <new_value>, <field2>: <new_value>, ...},
            ...
        }
    )

### Operators

* $set - Sets a new value to a field in a document
* $inc - Increments the value of the field by the specified amount.
* $push - Adds an item to an array.

### For example

###
    db.zips.updateOne(
        { "zip": "12534" },             // Filter Condition
        { "$set": { "pop": 17630 } }    // Set new value to "pop" field
    )

###
    db.zips.updateMany(
        { "city": "HUDSON" }, 
        { "$inc": { "pop": 10 } }
    )

###
    db.grades.updateOne(

        { "student_id": 250, "class_id": 339 },
        { "$push": { "scores": { 
                                "type": "extra credit", "score": 100 
                               }
                   }
        }
    )