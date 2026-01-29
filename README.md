# Tech-Challenge

## Requirement

```Using either AWS or GCP, create a website that displays some static text (you will not be judged on your HTML skills, and feel free to stick within the free/trial tiers for the resources you create). The text should include your name, for example, “This is Mary Smith’s website”```

## Solution

[Shadi Ferris Website](http://shadi-ferris-technical-challenge.s3-website-ap-southeast-2.amazonaws.com/)

## Summary

***What else you would do with your website, and how you would go about doing it if you had more time?***

What is the purpose of the website and who are the end users? The design and usability play an important role in ensuring the site meets the needs of its users. I would improve the overall aesthetics and usability by introducing a more pleasing layout, well-organised menus and headers, and integrate with enterprise search bar that could retrieve results from a secure data source. The website could also be integrated with a database to present content dynamically.

If I had more time, I would focus my efforts on the design phase to plan the infrastructure, layout, and usability. Once this was complete, I would begin building a minimum viable product MVP, using technologies such as HTML, PHP or Python, and SQL. I would continuously monitor the website’s performance during the build and deployment phases. Following deployment, I would iterate and release further enhancements.


***Alternative solutions that you could have taken but didn’t and explain why?***

There are many different approaches to setting up a website. For this attempt, I enabled AWS s3 static website hosting to expose the index.html file publicly. With more time, other approaches could have been considered, including:

Option 2: 
Register a new domain name using Amazon Roue53, deploy a web server (for example, Nginx, Apache Tomcat, or Apache HTTP Server) on an AWS EC2 instance within a public subnet, and configure security groups to allow SSH (port 22) and HTTP (port 80) access from the internet. This would also include configuring operating system and web server updates, deploying the website source code, setting up DNS records, and performing end-to-end testing.

Option 3:
Provision AWS infrastructure including a VPC, subnets, route tables, and an internet gateway for an EKS cluster. Configure security groups to allow HTTP traffic on port 80, deploy EC2 node groups or Fargate in a public subnet, and create a Dockerfile with the required web server image. This would involve copying HTML files into the appropriate directory, exposing port 80 in the container, building and pushing the image to AWS ECR, and creating Kubernetes Pod and Service YAML manifests. The Service could be configured as a NodePort or LoadBalancer, with port 80 exposed.

Based on the technical requirements, I chose the AWS S3 approach over the other options as it required the least time, effort, and cost. Given the three-hour time constraint for this challenge, the other options would have taken significantly longer due to the number of steps involved to provision infrastructure, setup and test. Option 2 could be completed more efficiently and at a lower cost compared to Option 3. Option 3 would require more effort and incur higher costs, however,it could be far more scalable in the long run compared to Options 1 and 2.

***What would be required to make this a production grade website that would be developed by various development teams. The more detail, the better?***


