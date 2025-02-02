# ADReports
Generate reports from Active Directory (AD).

## Description
ADReports provides tools to generate reports from Active Directory (AD) via LDAP. These can help you manage Active Directory by running certain reports (on a regular basis). This can be useful for:
* exporting data (e.g. getting a list of all users and using Excel to filter on certain fields)
* providing populations and/or evidence during audits (e.g. Due Diligence, Sarbanes–Oxley Act (SOX))
* cleanup actions (e.g. old or unused user accounts)
* inventory checks (e.g. find out which computers no longer log on)
* implementing procedures to improve compliancy (e.g. General Computer Controls (GCC), Sarbanes–Oxley Act (SOX))
* determining if home folders on a file server no longer belong to an active user
* getting information before problems occur (e.g. determine which user accounts are about to expire)

## Examples
* List all users on the console using the specified server, port and credentials:
  ```
  ADReportUsers -f TXT -h SERVER:389 -u MYLOGIN -p MYPASS
  ```
* Create Excel 2007 or higher .xlsx file with report containing all users:
  ```
  ADReportUsers -f XLSX -o All.xlsx
  ```
- Create Excel 2007 or higher .xlsx file with report containing all users created in the last 31 days:
  ```
  ADReportUsers -f XLSX -o CreatedLastMonth.xlsx -c 31
  ```
- Create Excel 2007 or higher .xlsx file with report containing all disabled users not logged in in the last 180 days:
  ```
  ADReportUsers -f XLSX -o Obsolete.xlsx -d -l -180
  ```
- Create Excel 2007 or higher .xlsx file with report containing all enabled users that expire in the next 32 days:
  ```
  ADReportUsers -f XLSX -o ExpiringNextMonth.xlsx -x 32 -e
  ```
- Create HTML file with report containing all users belong to any of the given groups:
  ```
  ADReportUsers -f HTML -o Admins.html -e -g "CN=Administrators,CN=Builtin,DC=DOMAIN,DC=LOCAL" -g "CN=Domain Admins,CN=Users,DC=DOMAIN,DC=LOCAL" -g "CN=Enterprise Admins,CN=Users,DC=DOMAIN,DC=LOCAL" -g "CN=Schema Admins,CN=Users,DC=DOMAIN,DC=LOCAL"
  ```
- Create HTML file with report containing all enabled users that have not logged in during the past 45 days:
  ```
  ADReportUsers -f HTML -o NotRecentlyLoggedIn.html -l -45 -e
  ```
- Create XML file with report containing all users in the specified OU:
  ```
  ADReportUsers -f XML -o DeleteMe.xml -b "OU=DeleteMe,OU=Company,DC=DOMAIN,DC=LOCAL"
  ```
- Create TSV (Tab Separated Values) file with report containing enabled all users that have "password never expires" enabled using a custom LDAP query:
  ```
  ADReportUsers -f TSV -o AccountNeverExpires.txt -e -q "(&(objectCategory=person)(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=65536))"
  ```