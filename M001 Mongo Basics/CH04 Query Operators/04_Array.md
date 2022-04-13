## Mongo field can contain array values, like

    {
        ...
        "bathrooms" : NumberDecimal("1.0"),
        "amenities" : [
            "TV",
            "Cable TV",
            "Wifi",
            "Kitchen",
            "Paid parking off premises",
            "Smoking allowed",
            "Pets allowed",
            "Buzzer/wireless intercom",
            "Heating",
            "Family/kid friendly",
            "Washer",
            "First aid kit",
            "Fire extinguisher",
            "Essentials",
            "Hangers",
            "Hair dryer",
            "Iron",
            "Pack ’n Play/travel crib",
            "Room-darkening shades",
            "Hot water",
            "Bed linens",
            "Extra pillows and blankets",
            "Microwave",
            "Coffee maker",
            "Refrigerator",
            "Dishwasher",
            "Dishes and silverware",
            "Cooking basics",
            "Oven",
            "Stove",
            "Cleaning before checkout",
            "Waterfront"
        ],
        "price" : NumberDecimal("80.00"),
        ...
    }

## Array Query Syntax

### To query 1 value in the array

    db.<collection_name>.find(
        {
            <array_field>: <array_value>
        }
    )

### To query multiple values in the array
#### use $all operator

    db.<collection_name>.find(
        {
            <array_field>: {
                "$all": [ <value1>, <value2>, ... ]
            }
        }
    )

### The $size operator matches any array with the number of elements specified by the argument

#### This will return array with 20 elements
    db.<collection_name>.find(
        {
            <array_field>: { $size: 20 }
        }
    )

#### This will return array with 20 elements and match the elements in $all list

    db.<collection_name>.find(
        {
            <array_field>: {
                $size: 20,
                "$all": [ <value1>, <value2>, ... ]
            }
        }
    )

## Lab 1

### Problem
What is the name of the listing in the sample_airbnb.listingsAndReviews dataset that accommodates more than 6 people and has exactly 50 reviews?

### Solution

    db.listingsAndReviews.find(
        { 
            "accommodates": { "$gt": 6 }, 
            "reviews": { "$size": 50 } 
        }
    )

### Result
    Sunset Beach Lodge Retreat

## Lab 2

### Problem
Using the sample_airbnb.listingsAndReviews collection find out how many documents have the "property_type" "House", and include "Changing table" as one of the "amenities"?

### Solution

    db.listingsAndReviews.find(
        {
            "property_type": "House",
            "amenities": "Changing table"
        }
    ).count()

### Result
    11

