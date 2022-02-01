# 4. Configuration provider

We try to adapt to your system and for this reason we have several parameters that we can configure for you in our system.

Parameter | Description | Recomendation
--------- | ----------- | ----------- 
Name | It is only a name. | Name of your system
Prefix | URL prefix | <a href="https://stackoverflow.com/questions/4357007/what-does-slug-mean">Slugify</a> of name of your system
Enabled | It works to disable very quicly the integration. | True
Send mail? | If you want that our system send emails.e.g.: After signup | False
Send sms? | If you want that our system send SMSs.e.g.: After signup | False
Available taxi types | XXXX |
Can request event services? | XXXX |
Self-validate phone? | If you want that our system validate the phone of your users or if you want that we trust in the validation in your system. | True
Self-validate email? | If you want that our system validate the e-mail of your users or if you want that we trust in the validation in your system. | True
Can passengers vote? | If you want that your users can vote yours services in our system | True
Skip reservation pickup date validation? | Our bookings has a minimum time to request. E.g.: No sense requesting a booking for in a minute. But if you want we can skip this validation | False
Allow fixed rate? | XXX |
Default company | Any passenger registered will be added to this company by default. This is for billing. If a passenger belongs to a company, so your system can request a taxi service on credit. | Your company
Allow companies | Your system can register a user of these companies. The difference with the previous attribute is that you can have several companies with different configurations. And you have to set the company of every passenger in the signup endpoint | None
Area | Your users may only request services in the area zones | None
Association | Any service requested by your users will be assigned to the indicated association | None
Always services for association | True: every service will be for the previous association. False: Only when pickup zone or destination zone will be a  zone of this association | False
Cost cancellation enabled | Cost cancellation only is applied when you cancel a service and the taxi is running to pickup point. | True
Cost cancellation enabled: required personal stripe | XXX | True


Also we have more configurations like differents request options or bill options. But we prefer talk about it in a private conversation.
