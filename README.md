# Auto Scaling in AWS and Hosting a Website on Nginx

This README provides step-by-step instructions for setting up auto-scaling in AWS and hosting a website separately on an Nginx server. The guide assumes basic familiarity with AWS services and Nginx.

## Part 1: Setting up Auto Scaling in AWS

### Step 1: Launch an EC2 Instance
1. Log in to the AWS Management Console.
2. Navigate to **EC2** > **Instances** > **Launch Instance**.

![Screenshot from 2024-12-27 19-51-29](https://github.com/user-attachments/assets/1474fe0c-1e53-49d9-8efc-af4f0abe55d1)


3. Select an AMI (e.g., Amazon Linux 2 or Ubuntu).

![Screenshot from 2024-12-27 19-52-48](https://github.com/user-attachments/assets/899423b5-2392-4b01-9d73-0a99ca17336f)


4. Choose the instance type (e.g., t2.micro) and create key pair.

![Screenshot from 2024-12-27 19-53-22](https://github.com/user-attachments/assets/51d9e7c7-5e80-471c-96f6-7990584a0889)

5. Configure the security group:
   - Allow SSH (port 22).
   - Allow HTTP (port 80).

![Screenshot from 2024-12-27 19-53-47](https://github.com/user-attachments/assets/13ba34d4-d62c-4065-bb6d-af7cc7f81472)
  
     
6. Launch the instance and note the Instance ID.

![Screenshot from 2024-12-27 19-54-06](https://github.com/user-attachments/assets/700ce6d6-d605-497e-b3f6-8670e52adaba)

### Step 2: Create a Launch Template
1. Navigate to **EC2** > **Launch Templates**.
2. Click **Create Launch Template**.

![Screenshot from 2024-12-27 19-55-03](https://github.com/user-attachments/assets/7d76fd18-36d9-4513-a0c8-ac81050c622e)

3. Provide a template name and select the AMI.

![Screenshot from 2024-12-27 20-01-02](https://github.com/user-attachments/assets/131e7a20-ccaa-49e5-ba55-56cba3a85fef)

![Screenshot from 2024-12-27 19-59-09](https://github.com/user-attachments/assets/3e8cea86-cac9-4915-829b-94f2bf2c63be)


4. Define instance type and other parameters.

![Screenshot from 2024-12-27 20-00-25](https://github.com/user-attachments/assets/a78608c2-2b82-4f12-b620-da535a1eb4d6)


5. Save the launch template.

![Screenshot from 2024-12-27 20-01-17](https://github.com/user-attachments/assets/1929b2ff-cda5-4635-8290-c08dd38029b6)


### Step 3: Configure an Auto Scaling Group
1. Navigate to **EC2** > **Auto Scaling Groups**.
2. Click **Create Auto Scaling Group**.

![Screenshot from 2024-12-27 20-01-31](https://github.com/user-attachments/assets/b655b7de-72a0-4b4a-9771-61513fc75166)

3. Select the launch template created earlier.

![Screenshot from 2024-12-27 20-01-57](https://github.com/user-attachments/assets/b00a92f2-1965-491a-8c84-7829b0e7b74f)
![Screenshot from 2024-12-27 20-02-34](https://github.com/user-attachments/assets/1b2c1661-1b73-43af-87d1-d10d47edc782)
![Screenshot from 2024-12-27 20-02-53](https://github.com/user-attachments/assets/9369f24b-4dcf-4287-8656-35b1da99e474)

4. Define the group size (minimum, maximum, and desired instances).

![Screenshot from 2024-12-27 20-03-43](https://github.com/user-attachments/assets/2c1c7abf-2324-4f15-9a1a-d474e1063fa8)
![Screenshot from 2024-12-27 20-03-51](https://github.com/user-attachments/assets/aa9aa2f3-7413-4d3c-9593-2325264c6c49)


5. Configure scaling policies (e.g., scale based on CPU utilization).
6. Attach a load balancer (optional).
7. Finalize and create the Auto Scaling Group.

![Screenshot from 2024-12-27 20-04-23](https://github.com/user-attachments/assets/ecdd8b06-6e2b-451b-957b-924b7d850dd6)
![Screenshot from 2024-12-27 20-04-39](https://github.com/user-attachments/assets/fa4c48cd-6369-4dc9-8ee9-97c259e939fe)

Notice: if you delete one of instance it auto launch the instances

![Screenshot from 2024-12-27 20-05-09](https://github.com/user-attachments/assets/fd1726b3-a0c4-41a9-9653-0ac145aef5aa)
![Screenshot from 2024-12-27 20-07-47](https://github.com/user-attachments/assets/df69bf48-a5fe-4164-a555-e7954ce3650b)


---

## Part 2: Hosting a Website on Nginx

### Step 1: Prepare the Server

![Screenshot from 2024-12-27 20-09-41](https://github.com/user-attachments/assets/4bade1fd-811a-4c28-89b4-b29530df1aa4)

1. Install Nginx on your server:
 
![Screenshot from 2024-12-27 20-16-30](https://github.com/user-attachments/assets/c1281892-5c6c-4248-b8e1-de142306218b)

![Screenshot from 2024-12-27 20-28-45](https://github.com/user-attachments/assets/1ceebcae-15b2-4411-be0e-9e775cb49733)



2. Start and enable Nginx:
 
![Screenshot from 2024-12-27 20-18-43](https://github.com/user-attachments/assets/a1c71803-5d14-406b-96a2-00136842f4a3)

### Step 2: Upload Website Files
1. Create the website directory:

![Screenshot from 2024-12-27 20-22-00](https://github.com/user-attachments/assets/dd78f1bb-6e6e-4334-a8f9-d57833c2bc78)

   
2. Upload your website files to `xyz/`.

![Screenshot from 2024-12-27 20-21-29](https://github.com/user-attachments/assets/46d84b46-2a9d-4a8d-9eb1-c26705737313)


3. Set permissions:
 
![Screenshot from 2024-12-27 20-32-00](https://github.com/user-attachments/assets/0fa379c1-9ab2-4401-bebf-062d25e043a2)
![Screenshot from 2024-12-27 22-48-25](https://github.com/user-attachments/assets/c9726724-cd0d-4252-ac8c-fef0b483d4be)

### Step 3: Configure Nginx
1. Navigate to the Nginx configuration directory:

![Screenshot from 2024-12-27 22-56-31](https://github.com/user-attachments/assets/3de61786-8a06-4355-88d8-9ea37bb09395)

2. Create a configuration file for your website:

![Screenshot from 2024-12-27 22-55-48](https://github.com/user-attachments/assets/54207062-a571-454d-bd29-65a2b478b240)

4. Add the following configuration:

 ![Screenshot from 2024-12-27 20-41-04](https://github.com/user-attachments/assets/9acc711b-3bb5-464c-8247-921ea0da1c92)

5. Test the configuration and restart Nginx:

 ![Screenshot from 2024-12-27 20-38-47](https://github.com/user-attachments/assets/ccd4f349-c3d7-4336-806a-3e9c7b2be471)


### Step 4: Access the Website
1. Open a browser and navigate to your server's public IP or domain name.
2. Verify that your website is accessible.

![Screenshot from 2024-12-27 20-41-30](https://github.com/user-attachments/assets/b290e36b-f63b-4bbb-b786-b4563042771f)

---

## Notes

- For production environments, consider using HTTPS with a certificate from Let's Encrypt.
- Monitor your Auto Scaling setup regularly to ensure proper scaling behavior.
- Use CloudWatch alarms to track application performance.

---

## Troubleshooting

1. **Nginx Not Starting**:
   - Check the configuration syntax:
     ```bash
     sudo nginx -t
     ```
   - Review the logs:
     ```bash
     sudo tail -f /var/log/nginx/error.log
     ```

2. **Auto Scaling Not Triggering**:
   - Ensure the scaling policies are configured correctly.
   - Verify IAM permissions for the Auto Scaling Group.

---

## Conclusion

By following this guide, you can set up a robust, auto-scaling infrastructure on AWS and host a website on a separate Nginx server. This approach ensures high availability and scalability for your applications.
