Sections

Format version
Description
Parameters - list of parameters used in the template. these values should be passed to create a stack out of the template.
Resources - list of resources to be provisioned
Outputs - list of items that should be available for access. ex: endpoint of the elb. this can be accessed to check the availability of the stack

A template:

Resources :

```
"S3Bucket": {
  "Type": "AWS::S3::Bucker",
  "Properties" : {
      AccessControl: "PublicRead",
      "WebsiteConfiguration:" ....
      ...
  },
  "DeletionPolicy": "Retain"
}
```

Outputs

WebsiteURL : {
"Value" : { .. .. . . .}
"Description": "url of website"
}
