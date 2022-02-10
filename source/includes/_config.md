# 4. Configuration provider

We try to adapt to your system and for this reason we have several parameters that we can configure for you in our system.

Parameter | Description | Recommendation
--------- | ----------- | ----------- 
Name | It is only a name. | Name of your system
Prefix | URL prefix | [Slugify][stackoverflow] of name of your system
Enabled | It works to disable the integration very quickly. | True
Send mail? | If you want our system send emails.e.g.: After signup | False
Send sms? | If you want our system send SMSs.e.g.: After signup | False
Available taxi types | The taxi types that your users can requests: conventional, six seats, eco, electric car, high-end, screen or adapted | e.g.: conventional and six seats
Self-validated phone? | If you want that our system validates the phone of your users or if you want that we trust in the validation in your system. | True
Self-validated email? | If you want that our system validates the e-mail of your users or if you want that we trust in the validation in your system. | True
Can passengers vote? | If you want that your users can vote your services in our system | True
Skip reservation pickup date validation? | Our bookings have a minimum time to request. E.g.: No sense requesting a booking for a minute. But if you want we can skip this validation | False
Default company | Any passenger registered will be added to this company by default. This is for billing. If a passenger belongs to a company, so your system can request a taxi service on credit. | This company has a lot of configuration too
Allow companies | Your system can register a user of these companies. The difference with the previous attribute is that you can have several companies with different configurations. And you have to set the company of every passenger in the signup endpoint | None
Area | Your users may only request services in this area | None
Association | Any service requested by your users will be assigned to the indicated association | None
Always services for association | True: every service will be for the previous association. False: Only when pickup zone or destination zone will be a  zone of this association | False

<aside class="notice">
Also we have more configurations like differents request options or bill options. But we prefer talk about it in a private conversation.
</aside>

<!-- Link section -->
  [stackoverflow]:  https://stackoverflow.com/questions/4357007/what-does-slug-mean