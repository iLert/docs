# Status pages

{% hint style="info" %}
**Closed beta phase**

Status Pages are currently available to selected customers as part of our early access program. Status pages will be generally available early this year.
{% endhint %}

## Set up your page

Creating a status is a matter of few clicks.

1\. Navigate to **Status pages** in the navigation bar and click on the **Create status page** button

2\. Select your page type, iLert URL and the teams that should manage the status page.

![](<../.gitbook/assets/Screen Shot 2022-03-10 at 17.03.42.png>)

3\. Select the services that you would like to include in the status page. You can also create new service and add them to the status page from the drop down list.

![](<../.gitbook/assets/Screen Shot 2022-03-10 at 17.17.06.png>)

4\. Optionally add your own logo and fav icon and click on **Save**.

5\. Click on the **Visit status page** button to preview your status page. Once you are satisfied with your status page, click on the **Activate** button to make your page available and viewable to your users.

![](<../.gitbook/assets/Screen Shot 2022-03-10 at 17.20.51.png>)

## Public vs. private status pages

Status pages in iLert can either be private or public. You change the page type any time. The table below compares both pages types:

|                                      | Public page                                                           | Private page                                                                                                                                                           |
| ------------------------------------ | --------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Use case**                         | For public incident communication with external users and customers   | For private incident communication with employees and customers that  have an iLert account. **Note that a stakeholder license is sufficient to view status pages.**   |
| **Visibility**                       | Publicly visible on the internet                                      | Visible to authenticated iLert users only                                                                                                                              |
| **Notification options**             | <ul><li>Email, SMS, Webhook</li><li>iLert user subscription</li></ul> | iLert user subscription                                                                                                                                                |
| **Supports custom domains with SSL** | :white\_check\_mark:                                                  | :white\_check\_mark:                                                                                                                                                   |

## Update the status of your status page

The status of your status page is automatically updated whenever

* the status of a service that is included in the status page is updated (e.g. by setting a service to _Degraded_)&#x20;
* an incident is created that affects any of the services from your status page

[--> How to create an incident](incidents.md#create-and-communicate-incidents)



## Automation with alert sources

You can automatically update your status page in the following ways:

* Automatically update the status of a service (for example set the status to _Degraded_)
* Automatically create an incident on your status page using an [incident template](incidents.md#create-an-incident-template) and (optionally) notify subscribers

Both cases work by using a service's automation rules. See [-> Services: automation with alert sources](services.md#automation-with-alert-sources) for more information.

## Setting up your custom domain <a href="#custom-domain" id="custom-domain"></a>

Every status page (both private and public) comes with support for custom domains, so that you can make your status page accessible from your own subdomains (e.g. status.example.com).&#x20;

Setting up a custom domain consist of the following steps:

1. Set the custom domain in iLert
2. Configure DNS
3. Wait for the changes to take effect

#### 1. Set the custom domain in iLert

Go to your status page settings and enter a custom domain and click on **Save**.

![](<../.gitbook/assets/Screen Shot 2022-03-14 at 16.19.12.png>)

#### 2. Configure DNS

Configuring DNS happens outside of iLert, at the DNS provider you are using for your domain.&#x20;

1. Create a new DNS record and select **CNAME** as the record type
2. Enter the name for the CNAME record. The **name** or **DNS entry** is where you enter your subdomain. You might need to enter it in full (e.g. **status.example.com**) or you might just need to enter the part before your apex domain (e.g. **status**). If you're not sure which to use, check with your DNS provider.
3. Enter the iLert URL of your status page as the value for the CNAME record. The **target** or **value** or **destination** is where the subdomain should be pointed. Taking the screenshot from above as an example, you would need to enter `ilert-demo.ilert.io` .

You might also see a field named **TTL**, which stands for Time To Live. It's the number of seconds that the DNS record can be cached for. If you're not sure what to set, look at the TTL for your existing DNS records. You could set the same number. If you're still not sure, we suggest setting 43200 seconds (12 hours) or 86400 seconds (24 hours).

{% hint style="warning" %}
**Are you using Cloudflare?**

Whenever possible, please **turn off Cloudflare proxying** (the orange cloud, also called "Proxy status" in your domain settings) to ensure that your status page is served without issues and can be monitored by iLert.
{% endhint %}

#### 3. Wait for the changes to take effect

You might need to wait 1-48 hours for the DNS changes to take effect. This depends on the TTL setting of your DNS record and the time it takes until the DNS change is propagated throughout the internet.&#x20;

## FAQ <a href="#faq" id="faq"></a>

#### I'm using iLert's uptime monitors. Can I connect an uptime monitor with a status page?

Yes, simply create a service and add an [automation rule](services.md#automation-with-alert-sources) that uses the uptime monitor's alert source.

#### We are a managed service provider and would like use multiple status pages to communicate incidents to different customers with private pages without exposing data between customers. Is that possible?

Yes. Our Premium plan even gives you unlimited stakeholder licenses. That way, you can invite as many customers as you need without requiring a full license.

To isolate customer's from each other, we recommend the following approach:

1. Create a team for every customer and make the team [private](../user-administration/teams.md#private-teams)
2. Invite your customer to iLert chosing the **Stakeholder** role
3. Add the customer to the respective customer team.
4. Assign the status page to the respective customer team.

#### I have set my status page to Public, but it's still not accessible from the internet. What am I missing?

You probably forgot to activate your status page. Once you are satisfied with your status page, click on the **Activate** button to make your page available and viewable to your users.

![](<../.gitbook/assets/image (59).png>)

&#x20;

