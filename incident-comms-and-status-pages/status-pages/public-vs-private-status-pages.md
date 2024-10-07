# Public vs private status pages

Status pages in ilert can either be private or public. You can change the page type at any time until the page was activated. Once activated, the page type cannot be changed. The table below compares both page types:

|                                                   | Public page                                                         | Private page                                                                                                                                                                                                                                  |
| ------------------------------------------------- | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Use case**                                      | For public incident communication with external users and customers | For private incident communication with employees, customers or partners that either have an ilert account, a whitelisted IP address or email address / email domain. **Note that a stakeholder license is sufficient to view status pages.** |
| **Visibility**                                    | Publicly visible on the internet                                    | Visible to authenticated ilert users only or to users with whitelisted IP addresses or email addresses / domains                                                                                                                              |
| **Supports custom domains with SSL**              | :white\_check\_mark:                                                | :white\_check\_mark:                                                                                                                                                                                                                          |
| **Supports IP Whitelist**                         | :x:                                                                 | :white\_check\_mark:                                                                                                                                                                                                                          |
| **Supports whitelisted emails and email domains** | :x:                                                                 | :white\_check\_mark:                                                                                                                                                                                                                          |

### Private status page authentication options

Only authenticated users can view ilert's private status pages. To adjust access, navigate to **Status Pages -> Authentication**, and select one or several authentication methods.

* **Accessible to all users of your account**: All users with any roles will have access to the chosen status page. Please note that the page will be visible even if it belongs to a private team.
* **IP Whitelist:** Specify IP addresses, and users without an ilert account will be able to see the status page.
* **Passwordless Email Login**: Enter email addresses and/or domains that should have access to your status page.
