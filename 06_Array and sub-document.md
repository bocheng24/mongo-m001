## Document field can contain document
### In sample_training.trips, there are 2 fields contain sub document
    {
        ...
        "start station location" : {
            "type" : "Point",
            "coordinates" : [
                -73.96150225,
                40.72057658
            ]
	    },
	    "end station location" : {
            "type" : "Point",
            "coordinates" : [
                -73.96525063,
                40.71044554
            ]
        },
        ...
    }

### To query sub-document field by name

    db.trips.findOne(
        { "start station location.type": "Point" }
    )

## Sub documents in an array

    {
        ...

        "relationships" : [
            {
                "is_past" : false,
                "title" : "CEO",
                "person" : {
                    "first_name" : "Valerio",
                    "last_name" : "Zingarelli",
                    "permalink" : "valerio-zingarelli"
                }
            },
            {
                "is_past" : true,
                "title" : "CTO",
                "person" : {
                    "first_name" : "Mallku",
                    "last_name" : "Caballero",
                    "permalink" : "mallku-caballero"
                }
            },

            ...
        ],

        ...
    }


### To query a specific sub-document in an array with index

    db.companies.find(

        { "relationships.0.person.last_name": "Zuckerberg" },
        { "name": 1 }

    ).pretty()

### Combine with $regex operator

    db.companies.find(
        {
            "relationships.0.person.first_name": "Mark",
            "relationships.0.title": { "$regex": "CEO" } 
        },
        { "name": 1 }
    ).pretty()

### Combine any sub-documents in an array that match conditions with $elemMatch operator

    db.companies.findOne(

        { 
            "relationships": { 
                "$elemMatch": { 
                        "is_past": true,
                        "person.first_name": "Mark" 
                    } 
                } 
        },

        { "name": 1 }

    ).pretty()

## Lab 1

### Problem
How many trips in the sample_training.trips collection started at stations that are to the west of the -74 longitude coordinate?

Longitude decreases in value as you move west.

Note: We always list the longitude first and then latitude in the coordinate pairs; i.e.

    <field_name>: [ <longitude>, <latitude> ]

### Solution

    db.trips.find(
        {
            "start station location.coordinates.0": { "$lt": -74}
        }
    ).count()

### Result
    1928

## Lab 2

### Problem
How many inspections from the sample_training.inspections collection were conducted in the city of NEW YORK?

### Solution

    db.inspections.find (
        {"address.city": "NEW YORK"}
    ).count()

### Result
    18279