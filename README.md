# Code Content generator console tool with input settings

This is an console application generates C# classes based on input Json Schema file.

The goal is to generate C# classes from Json Schema and parameters:
- Generate with Pascal case convention
- Include default namespaces

![image](https://github.com/curiousmindos/CodeGeneratorConsoleApplication/assets/7238801/0be55c38-6a13-4e68-9a07-7a4bd5c29772)


You can use this tool for your generated C# classes usage if you have only Json schema.

The sample to input Json Schema file and generated C# classes
```
{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "title": "BookingMessage",
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "Id": {
      "type": "string"
    },
    "endDate": {
      "type": "string",
      "format": "date-time"
    },
    "bookedByPerson": {
      "type": "string"
    },
    "tripId": {
      "type": "string"
    },
    "currencyCode": {
      "type": "string"
    },
    "Items": {
      "type": "array",
      "items": {
        "$ref": "#/definitions/Product"
      }
    }
  },
  "definitions": {
    "Product": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "ProductId": {
          "type": "string"
        },
        "rateCode": {
          "type": [
            "null",
            "string"
          ]
        },
        "Count": {
          "type": "integer",
          "format": "int32"
        },
        "ProductType": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/ProductType"
          }
        }
      }
    },
    "ProductType": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "Type": {
          "type": "string"
        },
        "Status": {
          "type": [
            "integer",
            "null"
          ],
          "format": "int32"
        }
      }
    }
  }
}
```

Generated C# classes
```
using System;
using System.Collections.Generic;
using System.Text;

namespace CodeGenerator.BookingMessage;

public class BookingMessage
{
	public string Id {get; set;}
	public DateTime EndDate {get; set;}
	public string BookedByPerson {get; set;}
	public string TripId {get; set;}
	public string CurrencyCode {get; set;}
	public ICollection<Product> Items {get; set;}
}

public class Product
{
	public string ProductId {get; set;}
	public string? RateCode {get; set;}
	public Int32 Count {get; set;}
	public ICollection<ProductType> ProductType {get; set;}
}

public class ProductType
{
	public string Type {get; set;}
	public Int32? Status {get; set;}
}

```

 

