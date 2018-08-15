# aws-static-website-hosting
This AWS CloudFormation template creates all necessarry resources to host a static website.

## Prerequisites
### Required
* At least one hosted zone in Route53.
* Rights for creating of all resources used in this template

### Optional
* a certificate in region us-east-1, which covers the domain



## Parameters
### DomainName 
The domain name parameter is used for creating a bucket as well as a record set which points to the CloudFront distribution.
    
    
### IndexDocument
The index document which is called if no other path is set in the request. 

*Default: index.html*
    
### ErrorDocument
The document which is returned in case of an error. 

*Default: error.html*

### Custom404ErrorPage
The document which is shown in case of a HTTP Error Code 404 Not Found. 

*Default: 404.html*

### PriceClass
Region and pricing plan for the CloudFront CDN Distribution. Allowed values are
* PriceClass_All
* PriceClass_200
* PriceClass_100

PriceClass_All is for worldwide distribution. This option is the momst expensive one. PriceClass_200 is worldwide distribution except of South America and Australia. PriceClass_100 is the cheapest option and used if the origin of your requests are usually in the US, the EU or in Canada. 

*Default: PriceClass_100*

### UseDefaultTLSCertificate
If you want to use a CloudFront default certificate (covering *.cloudfront.net) or not. You should never use a default certificate in a production environment. 

*Default: false*
  
  
### CertificateArn
The ARN of the certificate you want to use. This certificate has to be located in the region us-east-1 and needs to be verified. If UseDefaultTLSCertificate is *true* you can ignore this parameter. Otherwise it is mandatory.


### HostedZoneId
The ID of the Route53 hosted zone. In this hosted zone the record set will be created.


### LoggingBucket
The S3 bucket name where CloudFront logs will be stored.


### LoggingPrefix:
The prefix of the log files.

 *Default: cloudfront*

## Resources

## How To Install
### Via AWS Management Console
1. Open your AWS Management Console and Login to your account
2. Switch to the region where you want to deploy the infrastructure
3. Click on *Services*
4. Click on *CloudFormation*
5. Click on *Create Stack* button
6. Under *Choose a template* choose the option *Upload a template to Amazon S3*
7. Click on the *Browse...* button
8. Select the CloudFormation script (BasicStaticDistribution.yml)
9. Click on *Next* button
10. Insert the parameters and click on *Next*
11. Optionally you can add tags and configure CloudWatch alarms
12. Click on *Next* button
13. Review the information and click on *Create* button