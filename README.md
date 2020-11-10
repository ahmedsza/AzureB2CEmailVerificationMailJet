# Custom Email Verification in Azure B2C with MailJet - Policies Repo

## Background
This repo contains a set of policy files to implement Custom Email Verification using MailJet. It is based off the documentation at https://docs.microsoft.com/en-us/azure/active-directory-b2c/custom-email-mailjet. 

I had problems with some of the instructions on this page and the policy files at https://github.com/azure-ad-b2c/samples/tree/master/policies/custom-email-verifcation-displaycontrol/policy/Mailjet

Hopefully this will be of help to you

## Pre-requistes
- Azure B2C is setup appropriately

## Instructions
1. Follow the instructions at https://docs.microsoft.com/en-us/azure/active-directory-b2c/custom-policy-get-started to setup the relevant keys and app registrations
2. Clone this repo
3. Update TrustFrameworkExtensions.xml with the values of the app id obtained from the step 1
4. Follow the instructions at https://docs.microsoft.com/en-us/azure/active-directory-b2c/custom-email-mailjet to
	- Create a Mailjet account
	- Create Azure AD B2C policy key
	- Create a Mailjet template
  
   
  There is no need to follow the rest of the instructions on this page (except for point 5 below)
  
5. In TrustFrameworkBase.xml set the appropriate values
- Update the Messages.0.TemplateID InputParameter value with the ID of the Mailjet transactional template you created earlier
- Update the Messages.0.From.Email address value. Use a valid email address to help prevent the verification email from being marked as spam.
- Update the value of the Messages.0.Subject subject line input parameter with a subject line appropriate for your organization.

6. Open each XML file and replace AzureB2CTenant with the name of your B2C Tenant. There is typically 3 instances in each file. 

7. Upload the custom policy file in the following order.

		1. 	TrustFrameworkBase.xml
		2. 	TrustFrameworkExtensions.xml
		3. 	SignUpOrSignin.xml
		4. 	ProfileEdit.xml
		5. 	PasswordReset.xml
  
  See https://docs.microsoft.com/en-us/azure/active-directory-b2c/custom-policy-get-started#upload-the-policies for more

8. Test the policy. See https://docs.microsoft.com/en-us/azure/active-directory-b2c/custom-policy-get-started#test-the-custom-policy for information
  - Tip/Hint. I kept on going to the "default" flows to test (and getting very frustrated). You need to click the custom policy and the test.
