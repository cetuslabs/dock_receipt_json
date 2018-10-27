# Dock Receipt JSON 

Defines a JSON standard to communicate dock receipt information between parties.

## What is a dock reciept?

As defined on https://www.globalnegotiator.com/international-trade/dictionary/dock-receipt/

A receipt issued by a warehouse supervisor or port officer certifying that goods
have been received by the shipping company. The dock receipt is used to transfer
accountability when an export item is moved by the domestic carrier to the port
of embarkation and left with the international carrier for movement to its
destination. Dock receipts are normally prepared by forwarders or shippers.

## Example Dock Receipt JSON

```
{
  "dock_receipt_number" : "1234",
  "booking_number" : "10425335",
  "shipper_name" : "Big Company",
  "truck" : {
    "license_plate" : "1234",
    "company_name" : "Heat LLC."
  },
  "cargoes": [
    {
      "cargo_type" : "breakbulk",
      “package_type”: “BX”,
      "height" : "22",
      "length" : "44",
      "width" : "66",
      "dimension_unit" : "inch",
      "weight" : "400",
      "weight_unit" : "lb",
      "quantity" : 2,
      "description" : "Yamaha Generator",
      "hazmat_codes" : [
          {
            "code": "1050",
            "class": "2.3",
            "name": "Hydrogen chloride, anhydrous"
          },
          {
            "code": "1052",
            "class": "8",
            "name": "Hydrogen fluoride, anhydrous"
          }   
      ],
      "extras" : {
      }
    },
    {
      "cargo_type" : "vehicle",
      "height" : "220",
      "length" : "440",
      "width" : "660",
      "dimension_unit" : "inch",
      "weight" : "400",
      "weight_unit" : "lb",
      "quantity" : 1,
      "description" : "2017 Honda Accord, Turquoise",
      "hazmat_codes" : [],
      "extras" : {
        "vin": "1234",
        "make": "Honda",
        "model": "Accord",
        "year": "2017", 
        "color": "turquoise"
      }
    },
    {
      "cargo_type" : "boat",
      "height" : "220",
      "length" : "440",
      "width" : "660",
      "dimension_unit" : "inch",
      "weight" : "400",
      "weight_unit" : "lb",
      "quantity" : 1,
      "description" : "2017 Honday 105 Jet",
      "hazmat_codes" : [],
      "extras" : {
        "hin": "1234",
        "make": "Honda",
        "model": "105 Jet",
        "year": "2017", 
        "color": "navy blue"
      }
    }
  ]
}
```

## Attributes Defined:

| Attribute | Description |
| --- | --- |
| dock_receipt_number | Number to identify dock receipt |
| booking_number | Number to identify booking |
| shipper_name | Shipper Name |
| truck[license_plate] | License plate of truck that carried the cargo |
| truck[company_name] | The trucking company name of the truck that carried the cargo |
| cargoes | Array of cargo associated to dock receipt |


### Cargoes Attributes:
cargo_type: String to identify the type of cargo. Example: "breakbulk", "vehicle" and "boat".

height: Value to specify height of cargo

length: Value to specify length of cargo

width: Value to specify width of cargo

dimension_unit: Value to specify the unit used for the dimensions (feet, inches...) 

weight: Value to specify weight of cargo

weight_unit: Value to specify the unit used for the weight (lb,kg...)

quantity: Amount of items

description: A description of the cargo. Free text.

hazmat_codes[code]: The standard hazmat code

hazmat_codes[class]: The hazmat class related to the code

hazmat_codes[name]: The hazmat class name

extras: A key value pair of data. This can be any extra field the parties agree to use.

### The extras attribute
This is the object that should be able to give us the flexibility we will need.
In this object we can put any key value pair we agree on.
In the example above you can see that the vehicle and boat cargo have extra
values that the break bulk item doesn’t have.


### Extra Notes
All values will be send as a string except for the quantity value which is a
integer.
