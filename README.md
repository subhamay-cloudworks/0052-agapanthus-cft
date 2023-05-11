# Project Agapanthus: Working with Glue Data Catalog and Running the Glue Crawler On Demand

A user / producer uploads a json and a csv source file to a S3 bucket. A Glue crawler is run on demand to read the files and create a Glue database and store the metadata in Glue Data Catalog.

## Description

This project is a demonstration of AWS Glue crawlers to scan and create metadata definitions in the Glue Data Catalog. AWS Glue crawler connects to a data store, progresses through a prioritized list of classifiers to extract the schema of your data and other statistics, and then populates the Glue Data Catalog with this metadata. Crawlers could run periodically to detect the availability of new data as well as changes to existing data, including table definition changes. Crawlers automatically add new tables, new partitions to existing tables, and new versions of table definitions. You can customize Glue crawlers to classify your own file types.


![Project Agapanthus - Design Diagram](https://subhamay-projects-repository-us-east-1.s3.amazonaws.com/0052-agapanthus/agapanthus-architecture-diagram.png)

![Project Agapanthus - Services Used](https://subhamay-projects-repository-us-east-1.s3.amazonaws.com/0052-agapanthus/agapanthus-services-used.png)

## Getting Started

### Dependencies

* Create a Customer Managed KMS Key in the region where you want to create the stack.
* Modify the KMS Key Policy to let the IAM user encrypt / decrypt using any resource using the created KMS Key.

### Installing

* Clone the repository.
* Create a S3 bucket and make it public.
* Create the folders - 0052-agapanthus/cft/nested-stacks, 0052-agapanthus/cft/cross-stacks
* Upload the following YAML templates to 0052-agapanthus/cft/nested-stacks
    * glue-crawler-stack.yaml	
    * glue-database-stack.yaml
    * glue-iam-role-stack.yaml
    * s3-stack.yaml
* Upload the following YAML templates to 0052-agapanthus/cft/cross-stacks
    * custom-resource-lambda-stack.yaml
* Upload the following YAML templates to 0052-agapanthus/cft/
    * agapanthus-root-stack.yaml
* Create the cross-stack using the template custom-resource-lambda-stack.yaml by using the S3 url and pass the appropriate parameters. Note the cross stack name which you need to pass to the root stack.
* Create the entire using by using the root stack template agapanthus-root-stack.yaml by providing the required parameters and the s3 cross stack name created in the previous step.
* Use the KMS Key Id you have created in your account.

### Executing program

* Upload the sample csv and json files to the s3 bucket.
* Run the Glue Crawler.
* Check the two tables created in the Glue database.
* Query the data using Athena.

## Help

Post message in my blog (https://blog.subhamay.com)


## Authors

Contributors names and contact info

Subhamay Bhattacharyya  - [subhamoyb@yahoo.com](https://blog.subhamay.com)

## Version History

* 0.1
    * Initial Release

## License

None

## Acknowledgments

Inspiration, code snippets, etc.
* [AWS Glue Immersion Day ](https://catalog.us-east-1.prod.workshops.aws/workshops/ee59d21b-4cb8-4b3d-a629-24537cf37bb5/en-US/lab1/event-notification-crawler/)
