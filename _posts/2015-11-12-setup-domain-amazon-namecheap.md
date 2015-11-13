---
layout: post
title:  "Setup Domain with Namecheap and S3"
subtitle: "Step by step guide!"
date:   2015-11-12
---

I was recently working on a static website I wanted to host it in amazon s3 and setup the domain on namecheap.
  The process was fairly straightforward:

___


## Setup your s3 bucket 

1. Start by Creating a new S3 bucket, **make sure** that the bucket name matches the desired CNAME.
2. Upload your content to the bucket.
3. Add a bucket policy to allow anonymous read access to all objects in the bucket:


{% highlight json %}
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AddPerm",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR_BUCKET/*"
        }
    ]
}

{% endhighlight %}

YOUR_BUCKET: bucket name.

## Domain setup with Namecheap

1. SignIn to your namecheap account select the domain you want to link to your s3 bucket.
2. Go Into "Advanced DNS".
3. Add new record
- Type: CNAME
- Host: www
- Value Your bucket endpoint

Job Done, Have a beer.

