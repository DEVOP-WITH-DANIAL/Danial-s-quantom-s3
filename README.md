# Danial Raeen Najad's website

## This is a simple statis website which is hosted on an AWS S3 bucket. To view the website, please use [this link](http://danialsquantombucket.s3-website-ap-southeast-2.amazonaws.com/).

### **Replication Steps**

In order to replicate this website on youir own AWS envronment, please follow the steps below:

After making sure you're in the desired availability zone, on your AWS management console, click on S3, if you can't see the icon, you can simply use the search bar to find it:


![2023-05-23 14_49_28-AWS Management Console](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/2429d803-5f18-4b65-a087-3248479741d2)


Inthe opened window, click on **Create bucket**:
![2023-05-23 14_53_35-S3 Management Console](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/9437304b-2f09-41a2-a36e-8b06a101accc)

Type in your bucket name. Remember, S3 names are globally unique, meaning that two people can't use the same name for their bucket. In this instance, I picked **danialsquantombucket** . 
![2023-05-23 15_04_26-S3 bucket](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/328fe174-6794-4ea0-9034-1f595a893a07)


Since you already selected your region, you can leave the AWS Region tab as is and scroll down to **Block Public Access settings for this bucket** tab. Since this is a website that needs public access, you need to untick the **Block Public Access settings for this bucket** option and tick the aknowledgement box. 

![2023-05-23 15_11_19-S3 bucket](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/166f46b9-7527-4559-a135-a18c0f8c6d3e)


Ignore the rest of the options and click on **Create bucket** ![image](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/5e7815e7-0613-42aa-afad-370520a8211f)



After the bucket is created, click on the bucket name, and go to the properties tab on top, scroll all the way down and click on the Edit option on the **Static website hosting** tab. 

![2023-05-23 15_19_58-danialsquantombucket - S3 bucket](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/dd898c18-bc20-44e3-9875-0211121f6e62)

Click on the enable button and on the expanded tab, provide the name of the Index document and the Error document you have cloned from this repository. The error file is the name of the file which will be presented to the user when they try to navogate to a directory within your website which doesn't exit.
Leave the rest and click on save changes. 
![2023-05-23 15_38_38-danialsquantombucket - S3 bucket](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/4e49335b-a283-48a6-ac95-1c2e8f201f17)

Click on the Permissions tab on top and click on the Edit button in the Bucket Policy tab
![2023-05-23 15_44_25-danialsquantombucket - S3 bucket](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/06ce7126-026c-47b6-8e01-6b5dc599b594)

In the new tab, click on the **+Add new statement** button and edit the policy so it will contain the name of your bucket. After that, click on the save changes to save the policy. This policy allowes people who visit the website to have access to all of the assets within this bucket.


![2023-05-23 15_50_03-danialsquantombucket - S3 bucket](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/ac352a3f-90c8-454a-8cf9-891d7643b2a8)

Now we're going to upload the files which contains the website. Click on **Objects** tab and click on the **Upload** button. on the new window, click onupload files and select the index.html, error.html and quantom.html files you downloaded from this repository.



![2023-05-23 15_56_14-S3 Management Console](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/c90e53f0-1467-4932-9dd8-10e0d51bc5a5)



And that's it! you have successfully hosted a static website on AWS S3! In order to go your website, click on Properties tab and scroll all the way down. In the **Static website hosting** there is a URL which will redirect you to the website. 


![2023-05-23 16_03_41-danialsquantombucket - S3 bucket](https://github.com/DEVOP-WITH-DANIAL/Danial-s-quantom-s3/assets/87901858/2d101aed-072f-4bed-a2f6-153fc50093d3)


## Alternative solutions and why they were not considered for this project

**Hosting the website on an EC2 instead**

Using EC2 to host our website would have given us more control over our infrestructure and would have allowed us for more costomization which would have involved more setup and maintenance like configuring the web server and managing stability. For our case which is a simple static website, using an EC2 instance would be complex and time consuming.


**Using Elastic Beanstalk**

This service simplifies the deployment and management of the application. It manageas and provisionsour underlaying infrestructure automatically. But since our project is a simple static website, using Elastic Beanstalk would have been too much and its usually used for more complex apps which need scaling and more complicated configuration. 



## Additional improvements 

**below is a list of improvements which we can have consider for this project to make it a production grade website**

1. Improved design: We can improve the looks of our website by adding CSS styles to make it more appealing to our audience.

2. Domain name and SSL certificate: We can register a domain name and point it to our website. On top of that, we can obtain an SSL certificate to enable HTTPS access. This can be done by using tools such as **Route 53**, **AWS ACM**, and **cloudFront**

3. Monitoring: We could setup monitoring by using tools like AWS cloudWatch or external tools like DataDog to track the website's performance and user behaviour. 

4. Using CDN: Assuming our website is going to be global, we can consider integrating a content delivery network such as AWS CloudFront.

5. Setting up CI/CD: Using a CI/CD tools such as AWS CodePipeline or exernal tools like CircleCi, we can automate deployment and streamline the development process. We could also add additional tools in our CI pipeline to check for security vulnerabilities in our code before they get merged. 

6. Security considerations: applying additional security measures like setting up proper authentication and authorization mechanisms for users and engineers who use our assets could mitigate security breaches and data leaks. We could also set up AWS WAF to prevent any malicious attacks to our infrestructure.

7. Scalibility and availability: assuming our website is going to expect to handle high traffic or requires high availability, we could design our infrestructure for scalibility and redundancy by using tools like Aws Auto scaling. 
