# terraform-aws-cis-fundamentals

This Terraform module helps to setup an AWS account with the requirements of  CIS Amazon Web Services Foundations Benchmark v1.1.0

1. Identity and Access Management
    1. *Avoid the use of the "root" account (Scored)* - **Cannot be codified**
    2. Ensure multi-factor authentication (MFA) is enabled for all IAM users that have a console password (Scored)
    3. Ensure credentials unused for 90 days or greater are disabled (Scored)
    4. Ensure access keys are rotated every 90 days or less (Scored)
    5. Ensure IAM password policy requires at least one uppercase letter (Scored)
    6. Ensure IAM password policy require at least one lowercase letter (Scored)
    7. Ensure IAM password policy require at least one symbol (Scored)
    8. Ensure IAM password policy require at least one number (Scored)
    9. Ensure IAM password policy requires minimum length of 14 or greater (Scored)
    10. Ensure IAM password policy prevents password reuse (Scored)
    11. Ensure IAM password policy expires passwords within 90 days or less (Scored)
    12. Ensure no root account access key exists (Scored)
    13. Ensure MFA is enabled for the "root" account (Scored)
    14. *TODO*: Ensure hardware MFA is enabled for the "root" account (Scored)
    15. *Ensure security questions are registered in the AWS account (Not Scored)* **Cannot be codified**
    16. Ensure IAM policies are attached only to groups or roles (Scored)
    17. Enable detailed billing (Scored) **[Manual intervention 1](#action-1)**
    18. *TODO*: Ensure IAM Master and IAM Manager roles are active (Scored).
    19. Maintain current contact details (Scored) **Cannot be codified** **[Manual intervention 2](#action-2)**
    20. Ensure security contact information is registered (Scored) **Cannot be codified** **[Manual intervention 2](#action-2)**
    21. Ensure IAM instance roles are used for AWS resource access from instances (Not Scored)
    22. Ensure a support role has been created to manage incidents with AWS Support (Scored)
2. Logging
    1. Ensure CloudTrail is enabled in all regions (Scored)
    2. Ensure CloudTrail log file validation is enabled (Scored)
    3. Ensure the S3 bucket CloudTrail logs to is not publicly accessible (Scored)


# List of manual interventions
##### Action 1
AWS API does not support to set up billing reports and the section 1.17 only creates the necessary bucket. The rest should be taken care of manually.

After applying Terraform, a privileged user needs to take following actions
1. Open https://console.aws.amazon.com/billing/home?#/preference
2. Enable **Receive Billing Reports**
3. Type the name of the bucket you've created in section 1.17 into the textbox.
4. Click **Verify**
5. Click **Save preferences**

##### Action 2
AWS API does not support this action, so needs to be completed manually by the root user.
To find out what needs to be done, please visit https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-account-payment.html#contact-info
