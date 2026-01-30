# Tech-Challenge

## Requirement

```Using either AWS or GCP, create a website that displays some static text (you will not be judged on your HTML skills, and feel free to stick within the free/trial tiers for the resources you create). The text should include your name, for example, “This is Mary Smith’s website”```

## Solution

[Shadi Ferris Website](http://shadi-ferris-technical-challenge.s3-website-ap-southeast-2.amazonaws.com/)

## Summary

***What else you would do with your website, and how you would go about doing it if you had more time?***

What is the purpose of the website, and who are the end users? Design and usability play an important role in ensuring the site meets the user needs. I would improve the overall aesthetics and usability by introducing a more pleasing layout, well-organised menus and headers, and integrating an enterprise search bar that can retrieve results from a secure data source. I would also integrate various forms of digital media and imagery. The website could be further enhanced by integrating a database to present content dynamically.

If I had more time, I would focus my efforts on the design phase to plan the infrastructure, layout, and usability. Once this was complete, I would begin building a minimum viable product (MVP) using technologies such as HTML, PHP or Python, and SQL. For a long-term, mission-critical website, I would set up monitoring to observe metrics and performance during the build and deployment phases. Following deployment, I would iterate and release further enhancements.

***Alternative solutions that you could have taken but didn’t and explain why?***

There are many different approaches to setting up a website. For this attempt, I enabled AWS s3 static website hosting to expose the index.html file publicly. With more time, other approaches could have been considered, including:

Option 2: 
Register a new domain name using Amazon Roue53, deploy a web server (for example, Nginx, Apache Tomcat, or Apache HTTP Server) on an AWS EC2 instance within a public subnet, and configure security groups to allow SSH (port 22) and HTTP (port 80) access from the internet. This would also include configuring operating system and web server updates, deploying the website source code, setting up DNS records, and performing end-to-end testing. Alternatively to the Route53 option, I could have viewed the webpage via the EC2 public IPv4 DNS address.

Option 3:
Provision AWS infrastructure including a VPC, subnets, route tables, and an internet gateway for an EKS cluster. Configure security groups to allow HTTP traffic on port 80, deploy EC2 node groups or Fargate in a public subnet, and create a Dockerfile with the required web server image. This would involve copying HTML files into the appropriate directory, exposing port 80 in the container, building and pushing the image to AWS ECR, and creating Kubernetes Pod and Service YAML manifests. The Service could be configured as a NodePort or LoadBalancer, with port 80 exposed.

Based on the technical requirements, I chose the AWS S3 approach over the other options as it required the least time, effort, and cost. Given the three-hour time constraint for this challenge, the other options would have taken significantly longer due to the number of steps involved to provision infrastructure, setup and test. Option 2 could be completed more efficiently and at a lower cost compared to Option 3. Option 3 would require more effort and incur higher costs, however,it could be a far more scalable website solution for the long term compared to Options 1 and 2.

***What would be required to make this a production grade website that would be developed by various development teams. The more detail, the better?***

To make the website more production-grade, while also allowing development teams the autonomy to build, deploy, and test safely, I would begin at the AWS account management level by setting up an AWS Landing zone architecture. This would enable teams to build, deploy, and test workloads in isolation, while providing the business with oversight of billing, security controls, and resource limitations.

Following Landing zone setup, the target state of the website would include a multi-availability zone AWS EKS Cluster, leveraging Kubernetes orchestration, scaling, and container management capabilities by default. All infrastructure provisioning would be implemented using Infrastructure as Code (e.g. Terraform) to ensure services such as VPCs, subnets, route tables, NAT gateways, internet gateways, security groups, users, IAM roles, KMS, EKS clusters, and node groups are deployed automatically and consistently across AWS accounts.

At the node, pod, and container levels, I would implement the following measures to ensure availability and resiliency for the website:
	•	Provision Kubernetes clusters and nodes across multiple Availability Zones (and regions where required) to achieve high availability and minimise user latency.
	•	Create namespaces to separate development, testing, and production environments, and apply resource quota policies to manage team resource usage.
	•	Configure website deployments with a minimum of two pod replicas to ensure redundancy and availability in the event of node or Availability Zone failures.
	•	Implement Kubernetes Horizontal Pod Autoscaling to automatically scale workloads based on CPU and memory utilisation, ensuring capacity adjusts to demand.
	•	Apply Pod anti-affinity rules to ensure that website pods are not scheduled on the same node.
	•	Apply Node affinity rules to ensure website pods are scheduled only on nodes that meet specific criteria.
	•	Configure appropriate terminationgraceperiodseconds and prestop hooks to allow pods to shut down gracefully.
	•	Ensure all website pods use a restartpolicy of always to automatically recover from unexpected failures.
	•	Configure liveness and readiness probes to ensure traffic is only routed to healthy pods.
	•	Implement SSL/TLS certificates via ingress controllers to securely expose website services publicly.
	•	Deploy web services across multiple regions where required, using traffic-routing strategies to minimise latency.

To ensure end-to-end reliability, sufficient monitoring and alerting would be implemented, including:
	•	Monitoring infrastructure, platform, and application metrics such as traffic, latency, error rates, saturation, node health, and pod performance.
	•	Capturing telemetry and user-experience metrics (for example, page load times and error rates) to focus on speed, reliability, and responsiveness.
	•	Define the business level SLA’s, and create and track corresponding SLO’s and SLI’s.

Finally, automated functional and non-functional testing would be integrated into the CI/CD pipeline, including end-to-end tests across all components and dependent services to simulate real user interactions.

