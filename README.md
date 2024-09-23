# Multi-Cloud Identity and Access Management (IAM) Framework

## Overview

This project demonstrates how to integrate **AWS IAM** and **Azure Active Directory (Azure AD)** to create a **multi-cloud Identity and Access Management (IAM) framework**. The goal is to securely manage user access across both AWS and Azure environments, leveraging **SAML-based federated access** and implementing security best practices such as **MFA**, **least privilege** access control, and **conditional access policies**.

Link to Video Outlining Steps:
https://youtu.be/S0_wozfkBXY



[![Watch the video](https://img.youtube.com/vi/S0_wozfkBXY/hqdefault.jpg)](https://youtu.be/S0_wozfkBXY)



## Architecture

The project integrates AWS IAM and Azure AD through SAML-based federated access, allowing Azure AD users to authenticate and assume roles in AWS. The architecture consists of:
- **AWS IAM**: User roles and policies to manage access to AWS resources.
- **Azure Active Directory (Azure AD)**: Central identity provider managing user authentication and access control across Azure services.
- **SAML Federation**: Azure AD acts as the identity provider (IdP), allowing users to log into AWS and assume predefined roles.

## Project Features

- **Role-Based Access Control (RBAC)** in AWS and Azure
- **SAML Federation** between Azure AD and AWS IAM
- **Multi-Factor Authentication (MFA)** enforcement
- **Least Privilege Access** across AWS and Azure
- **Conditional Access Policies** in Azure AD
- **Cross-cloud Monitoring** using AWS CloudTrail and Azure AD auditing

---

## Prerequisites

- **AWS Account** with IAM permissions to create roles and manage identity providers.
- **Azure AD** subscription with permissions to create enterprise applications and configure SAML-based Single Sign-On (SSO).
- **Admin access** to both AWS and Azure environments.
  
### Tools
- AWS CLI or AWS Management Console
- Azure CLI or Azure Portal

---

## Project Setup

### Step 1: AWS IAM Setup

1. **Create IAM Roles** for federated access in AWS:
    - Go to the **IAM** section in AWS and create new roles for your users (e.g., Admin, Developer, Viewer).
    - Assign the necessary permissions (e.g., Admin = full access, Developer = EC2, Lambda, S3 only).
    - Configure a **Trust Relationship** with the Azure AD identity provider (SAML).

2. **Enable MFA** for all IAM users:
    - Enforce MFA for sensitive actions and logins.
    - Use **AWS IAM policies** to restrict user actions based on MFA status.

### Step 2: Azure AD Setup

1. **Create Users and Groups**:
    - Organize users into groups based on roles (Admin, Developer, Viewer).
  
2. **Configure Role-Based Access Control (RBAC)** in Azure:
    - Assign permissions to users for accessing Azure resources based on their group memberships.

3. **Create SAML Enterprise Application**:
    - In **Azure AD**, create a new non-gallery enterprise application for AWS.
    - Configure **SAML-based Single Sign-On (SSO)**.
    - Upload AWS metadata for SAML configuration.

### Step 3: SAML Federation between AWS and Azure AD

1. **Set up SAML in AWS**:
    - Go to **IAM > Identity Providers** in AWS.
    - Create a new SAML provider using Azure AD metadata.
  
2. **Configure Azure AD SAML Settings**:
    - In **Azure AD > Enterprise Applications**, configure the SSO settings to match AWS.
    - Set the **Identifier (Entity ID)** to `https://signin.aws.amazon.com/saml` and the **Reply URL** to `https://signin.aws.amazon.com/saml`.

3. **Map Azure AD Groups to AWS IAM Roles**:
    - Map Azure AD users to specific AWS roles (e.g., map the Admin group in Azure to the Admin role in AWS).
    - Use the `https://aws.amazon.com/SAML/Attributes/Role` attribute in Azure to specify the AWS role to assume.

### Step 4: Implement Security Policies

1. **Principle of Least Privilege**:
    - Review and minimize permissions for each role in both AWS and Azure.

2. **Conditional Access Policies in Azure AD**:
    - Set up conditional access policies to restrict access to AWS based on location, device compliance, etc.

### Step 5: Test and Validate

1. **Log in to AWS using Azure AD credentials**:
    - Test user logins and ensure the correct AWS roles are assumed based on Azure AD group membership.

2. **Validate Security Policies**:
    - Verify MFA enforcement, least privilege access, and conditional access policies are functioning as expected.
  
3. **Review Logs**:
    - Use AWS CloudTrail and Azure AD logs to review user activity and monitor for any security breaches.

---

## Security Enhancements

- **Enable MFA for Federated Access**: In Azure AD, require MFA for users accessing AWS.
- **Configure AWS CloudTrail for Auditing**: Ensure all API calls and federated logins are logged and monitored.
- **Implement IP Whitelisting**: Use IAM policies and Azure AD conditional access policies to restrict login access by IP range.

---

## Architecture Diagram

*Include an optional architecture diagram that shows the flow between Azure AD and AWS IAM, the federated login process, and the roles assumed by users in AWS.*

---

## Project Demonstration

Here’s a quick walkthrough video or link to a presentation/demo showing:
1. How users log in to AWS via Azure AD.
2. How roles and permissions are enforced across both clouds.
3. How MFA and conditional access policies improve security.

---

## Future Enhancements

- Integrating **Google Cloud Identity** for a tri-cloud IAM solution.
- Adding **automated user provisioning** across AWS and Azure using SCIM.
- Enhancing security with **Just-In-Time (JIT)** access for temporary elevated permissions.

---

## Conclusion

This project showcases a secure and scalable way to manage identities and access controls across multi-cloud environments, leveraging Azure AD and AWS IAM. With SAML federation, RBAC, and security best practices, this IAM framework enhances the security posture of any multi-cloud infrastructure.

---

## References

- [AWS Identity and Access Management (IAM) Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/)
- [Azure Active Directory SSO Documentation](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/sso-application-gallery)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Contact

If you have any questions, feel free to reach out to me at [your email] or connect on [LinkedIn].
