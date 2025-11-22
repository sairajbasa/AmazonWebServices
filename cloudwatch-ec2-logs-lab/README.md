# CloudWatch EC2 Logs Lab

This lab explains how I sent EC2 system logs to AWS CloudWatch Logs using the CloudWatch Agent.

### Objective
The goal of this lab is to push system log files from an EC2 instance to CloudWatch Logs so that the logs can be viewed and monitored from the AWS console.

### Steps I followed

1. I launched an EC2 instance
   - I used Amazon Linux.
   - I assigned an IAM role to the EC2 instance so that it can send logs to CloudWatch.
   - The IAM role had the CloudWatch permissions (CloudWatchFullAccess).

2. I installed the CloudWatch Agent on the EC2 instance
   - The agent is required to collect and send logs to CloudWatch.

3. I created the CloudWatch Agent configuration file
   - In the config file, I added the log file path (`/var/log/cloud-init.log`), log group name, log stream name, and AWS region.

4. I started the CloudWatch Agent service
   - After starting the service, it immediately began sending logs to CloudWatch.

5. I verified in the CloudWatch console
   - The log group was visible.
   - The log stream appeared with the EC2 instance ID.
   - The system log contents were visible in CloudWatch Logs.

### Result
My EC2 system logs were successfully pushed to CloudWatch Logs.  
After this setup, any new system logs generated in EC2 automatically appear in CloudWatch.

### What I learned
- IAM role is required for EC2 to communicate with CloudWatch.
- CloudWatch Agent collects log data from the EC2 instance.
- The configuration file controls where logs are taken from and how they appear in CloudWatch.
- CloudWatch helps monitor EC2 logs without logging into the instance.

### Next Plan
In future labs, I plan to:
- Push Tomcat or application logs to CloudWatch
- Create metric filters and CloudWatch alarms based on log patterns
- Create dashboards and automation using CloudWatch
