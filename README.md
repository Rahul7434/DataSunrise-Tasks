# DataSunrise-Tasks

##### Configuring Audit Trail for auditing MS Azure MySQL database queries
To configure DataSunrise to receive auditing results of Azure-hosted MySQL database activity, log in into Azure portal and
do the following:
```
1. Navigate to App registrations → New registration and register your application. Note that Redirect URI (optional) is
not required

2.At the API permissions page, click Add a permission

3.In the Microsoft APIs tab, select Azure Storage then select Delegated permissions and user_impersonation. Click Add
permissions to apply the changes

4.Navigate to your app registration. Select Certificates and secrets
5.At Client secrets, click New client secret to create a new secret. Save the VALUE key somewhere
6.Navigate to Resource groups and create a Resource group
7.Navigate to Storage accounts and create an Account
8.Select your Resource group and specify a Storage acount name. Leave all other settings as by default
9.Navigate to Access Control (IAM). Click Add role assignment
10.Select Reader: Next
11.Click +Select members and select your App. Review and assign
12.Click Add role assignment again and select Storage Blob Data Reader
13.Click +Select Members and select your app. Review and assign
14.Navigate to All Services → Azure Database for mysql servers and create a new server: Navigate to Create → Flexible
server → Create
15.Provide all the required server details
16.At the Networking tab, check Allow public access… and add required firewall rules. Complete the deployment
17.Navigate to your mysql database → Server Parameters and enable audit_log_enabled
18.Select event types to be logged by configuring audit_log_events
19.Add mysql users to be included in or excluded from logging by configuring audit_log_exclude_users and 
audit_log_include_users respectively. Save the settings
20.Navigate to Diagnostic settings → Add
21.Check MySqlAuditLogs and Archive to a storage account and select your Storage Account
22.Open DataSunrise’s Web Console and create a mysql Instance in Configuration → Databases. Select Trailing the DB
Audit Logs in the Instance’s settings
23.Copy ClientID and TenantID from your Azure App
24.Client Secret is the VALUE mentioned in step 5
26.You can find Blob container name in Storage Accounts - Your account → Containers of your Azure settings
26.Create some Audit Rules to get the logs. For auditing results, navigate to Audit → Transactional trails
```
