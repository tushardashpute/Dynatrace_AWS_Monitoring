# Dynatrace_AWS_Monitoring

**Enabling access to your Amazon account using key-based access**

Dynatrace can use access keys to make secure REST or Query protocol requests to the AWS service API. You'll need to generate an Access key ID and a Secret access key that Dynatrace can use to get metrics from Amazon Web Services.

1. Monitor EC2 instance using Dynatrace
2. Monitor AWS account using Dynatrace
3. Monitor EKS cluster using 

**1. Monitor EC2 instance using Dynatrace**

Steps:

a. Deploy one-agent on EC2 instance

![image](https://user-images.githubusercontent.com/74225291/210523052-4232d833-9af8-491b-90e5-54c2fc617ac7.png)

![image](https://user-images.githubusercontent.com/74225291/210523208-9bcc44c1-c1c7-472e-b9ba-d563501eb0c6.png)

Enter the paas token if you have already else you can create new token.

![image](https://user-images.githubusercontent.com/74225291/210523668-bdb873ae-2260-4cda-9727-98a439d7b821.png)

![image](https://user-images.githubusercontent.com/74225291/210524001-9c31423f-556c-43be-bcdb-60812d4d4a2b.png)

![image](https://user-images.githubusercontent.com/74225291/210524119-42327c0e-1741-41c8-a57a-65a857760693.png)

Once we are done with the steps showen in the above image, EC2 host metrices will be integrated with the Dynatrace:

![image](https://user-images.githubusercontent.com/74225291/210526095-abcaecd8-ac83-4744-8778-c657582dd8b1.png)

Now we can see all the metrices of the EC2 instance.

![image](https://user-images.githubusercontent.com/74225291/210526431-f2710c8d-6df9-448d-9e30-9e8825db39dd.png)

![image](https://user-images.githubusercontent.com/74225291/210526678-cfb59b54-3e47-4e54-ba21-65475c0aa043.png)

Currently we done have any thing running on the EC2 instance except ssm agent, now we can deploy some application on it and try to monitor it.


