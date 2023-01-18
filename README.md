For Continuous deployment on Elastic Beanstalk, prepare your AWS as this:

1. Create ElasticBeanstalk App (VPC & Security Group with Inbound HTTP rule is set automatically)
2. Create AWS RDS Postgress service in same VPC and set (and note!) user, password and database name
3. Create AWS Elasticache Redis Service in same VPC
4. Create custom Security Group with custom rule to allow Inbound traffic on necessary ports (here: 6379 & 5432)
5. Apply Security Group to each service inside VPC
6. Apply env variables to ElasticBeanstalk Environment as defined in the docker-compse.yml => for hosts: use primary service endpoints (without the port at the end)
7. Create new AWS IAM User for application and give permisson policy to deploy to ElasticBeanstalk (ElasticBeanstalk Admin Rights)
8. Set created AWS IAM ACCESS credentials in travis app environment variables
9. Update .travis.yml data under 'deploy' section
