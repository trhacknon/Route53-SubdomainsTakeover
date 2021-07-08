# Route53 - Subdomains takeover

[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)
[![Twitter](https://img.shields.io/twitter/url/https/twitter.com/cloudposse.svg?style=social&label=%40syed_umar)](https://twitter.com/syed__umar)

[contributors-shield]: https://img.shields.io/github/contributors/Anon-Exploiter/Route53-SubdomainsTakeover.svg?style=flat-square
[contributors-url]: https://github.com/Anon-Exploiter/Route53-SubdomainsTakeover/graphs/contributors
[issues-shield]: https://img.shields.io/github/issues/Anon-Exploiter/Route53-SubdomainsTakeover.svg?style=flat-square
[issues-url]: https://github.com/Anon-Exploiter/Route53-SubdomainsTakeover/issues

A script to fetch all route53 hosted zones, fetch all CNAME DNS records of each zone (domain) then check all the records containing elasticbeanstalk applications -- **if they're takeoverable** -- and post all that on Slack!  

***This is readme for installation on AWS lambda -- Visit master branch for running on CLI!**

### Tested On (OS & Python version)
- AWS Lambda - Python 3.8 

### Installation on Lambda

First of all pull the **layers** below and upload and create in your AWS account: 
- https://github.com/Anon-Exploiter/Route53-SubdomainsTakeover/releases/download/0.1/route53-subdomain-takeover-layer.zip
- https://github.com/Anon-Exploiter/Route53-SubdomainsTakeover/releases/download/0.1/awscli-lambda-layer.zip

Now go ahead and create a **lambda function** with a new role. After creation of the IAM role, edit it's permissions and add the following policy:
- `AmazonRoute53ReadOnlyAccess`

After creation of Lambda function and adding of layers, upload the following from the `aws-lambda` branch of GitHub:
- lambda_function.py

Now, create the following environmental variables (not required -- if `region` isn't specified default gets to `eu-west-1` and if no `webhook` is passed, nothing will be posted in slack -- the script still executes)
- WEBHOOK_URL
- REGION

`REGION` -> is the AWS region we want to work with -- While `WEBHOOK_URL` contains the Slack channel WebHook URL to post to.

### Filing Bugs/Contribution

Feel free to file a issue or create a PR for that issue if you come across any.
