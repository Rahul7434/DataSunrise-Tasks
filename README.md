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
##### Configuring Audit Trail for auditing MS Azure PostgreSQL database queries
To configure DataSunrise to receive audit results of Azure-hosted PostgreSQL database activity, do the following:
```
1.Navigate to App registrations → New registration and register your application. Note that Redirect URI (optional) is not
required
2.Navigate to your app registration. Select Certificates and secrets
3.At Client secrets, click New client secret to create a new secret. Save the VALUE key
4.At API permissions select Add permission → Azure Storage → Delegated permissions then user_impersonation then
click Add permissions
5.Configure your postgresql flexible server’s settings:
  log_checkpoints = OFF
  log_destination = CSVLOG or JSON
  pgaudit.log = ALL
  shared_preload_libraries = PG_STAT_STATEMENTS, PGAUDIT
  log_line_prefix = %t-%c-u"%u"u

6.Enable diagnostic settings for your postgresql server using either the Azure portal, CLI, REST API, or PowerShell. The
log category to select is PostgreSQLLogs. See the next step for a guide on using Azure portal for that
7.In Azure portal, navigate to Monitoring → Diagnostic settings of your postgresql server. Click Add Dianostic Setting.
Fill out all the required fields. Select log type PostgreSQLLOgs. In Destination details, select Archive to a storage account
and select your Storage account. Save the setting
8.Assign an Azure role for access to BLOB data (Reader and Storage BLOB Data Reader for the app created earlier)
9.Navigate to Access Control (IAM). Click Add role assignment
10.Select Reader: Next
11.Click +Select members and select your app. Review and assign
12.Click Add role assignment again and select Storage Blob Data Reader
13.Click +Select Members and select your app. Review and assign
In DataSunrise, do the following:
14.Create a postgresql Instance in Configuration → Databases. Select Trailing the DB Audit Logs in the Instance’s settings
15.Copy ClientID and TenantID from your Azure App
16.Client Secret is the VALUE mentioned in step 3
17.You can find Blob container name in Storage Accounts - your account → Containers of your Azure settings
18.Paste the Server Name, the name of the database server, and the Resource Group Name where the database server is
located
19.Create some Audit Rules to get the logs. For auditing results, navigate to Audit → Transactional trails
```
