# FOR2-AccessDenied

FOR2 Tracking a suspicious system activity.

a. We make a list few system resources, if user or any application tries to access or modify these resources, then alert the system admin via email.

b. Admin should get notification for each user login.

c. If too many failed log-in attempt from a particular client, inform the admin.

## Prerequisite

The script is made for ubuntu 18.10

## Commom Components

We are using postfix for mail server. The email will be send to the email of admin provided during setup.
The Heroku API, Sender E-Mail, Sender Password, Admin API need to passed by cmd arguments in the security-setup script.

For Example:
```sudo ./security-setup -e [admin-email] -a [heroku api] -s [Sender E-Mail] -p [Sender Password]```

We also have security-setup -h for help menu.

## Main Script

security-setup is the main script which will be responsible for all the setup.

## login-alert

When the user logs in, This script will send mail to admin and send the data to heroku where we are storing it in hasura graphql.

## failed-login-alert

When the system detects bad login, This script will send mail to admin and send the data to heroku where we are storing it in hasura graphql.

## Task Completed

login-alert is working perfectly for all the user logins
failed-login-alert is working perfectly for all the bad logins
check-modify will check the resources mentioned in the configuration file "/etc/security-setup/check-modify.conf" if the user access or modified it.

All the scenerios will send email and data to hasura database. 

## Troubleshooting

If you see error about postfix service not restarting please reboot the system and try again.

## Please Note

Do not run the security-setup script twice.
