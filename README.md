# Code Content generator console tool with input settings

This is an console application generates C# classes based on input Json Schema file.

The goal is to generate C# classes from Json Schema and parameters:
- Generate with Pascal case convention
- Include default namespaces

You can use this tool for your generated C# classes usage if you have only Json schema.

1. The sample to input Json Schema file and generated C# classes
```
{
  "httpMethod": "GET",
  "urlEndpointPath": "/my-customer-url-v2",
  "responseMessage": "Single Response with This URL Request",
  "httpStatusCode": 200,
  "latencyInMilliseconds": 300
}
```

 

