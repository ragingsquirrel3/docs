## Customization 

### Customize Object Key Path 

You can customize your key path by defining custom prefix resolution for your requests.

<inline-fragment platform="ios" src="~/lib/storage/fragments/ios/configureaccess/50_custom_prefix.md"></inline-fragment>
<inline-fragment platform="android" src="~/lib/storage/fragments/android/configureaccess/50_custom_prefix.md"></inline-fragment>
<inline-fragment platform="flutter" src="~/lib/storage/fragments/flutter/configureaccess/50_custom_prefix.md"></inline-fragment>

For example, if you want to enable read, write and delete operation for all the objects under path *myPublicPrefix/*,  declare it in your IAM policy:

```xml
"Statement": [
    {
        "Effect": "Allow",
        "Action": [
            "s3:GetObject",
            "s3:PutObject",
            "s3:DeleteObject"
        ],
        "Resource": [
            "arn:aws:s3:::your-s3-bucket/myPublicPrefix/*",
        ]
    }
]
```

If you have IAM policies with an existing bucket, See [Use an existing S3 bucket](~/cli/storage/import.md) for more details.