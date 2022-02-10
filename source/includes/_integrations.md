# 2. Integration types

You can integrate with us in several ways. In this documentation, we will focus on Server to server integration, but you must know that you can connect with us from client to server. In client to server integration the endpoints are the same, almost everything is the same, but for example the [AAI][aai] (Authentication and authorization infrastructure) is different or we don't need an own [push system][push].

## 2.1 Client to server

You can choose between two ways:

    - Own development. You can create a Web or App and connect with this API
    
    - We can clone our web or/and our app for you with several customizations. We can do it very quickly :-)


## 2.2 Server to server


### 2.2.1 Where to start?

There are several endpoints in this documentation, but there is only one mandatory endpoint: [Create Service][create-service]. But if do you want do an integration more rich we have another endpoints to use

By importance, the next endpoint is to [Cancel service][cancel-service]. It is not mandatory, but it is very recommended if you want to cancel a service after request.

If your services may be modified after request them, so you should be use [Edit service][edit-service]

You can use a generic user for the integration or you can use a specific user for every request. So, if you want to request a service to `John Smith`, you will create ([signup][signup]) a user for `John Smith` in our system the first time, and after it you will create a service in our system. If `John Smith` wants another service, you do not have to create a user the next time. See more info in [AAI][aai] section.

To track services we recommend to use [Current endpoint][current-service]. Although we enable [push notifications][push], polling is highly recommended. We recommend you to call to this endpoint every 30 seconds or one time per minute for good feedback about your services.

### 2.2.2 Where to continue?

If you want to go deeper into the integration. We recommend you to use [Zone][zone]. Every zone has a configuration. The configuration is not the same in a big city than in a little city or a town, in the downtown of a city than in the suburbs of a city, in an airport than in another airport

With [Zone endpoint][zone], you can knows the available taxi types (conventionals, six seats, ecos, electrics, high-ends, adapteds, etc), if you can request an immediate service, if there is cost cancellation in this zone, if destination is required, min time to request a reservation, etc

But if you want to request only conventional taxis, and you can request them within a reasonable time... Really, this endpoint is not necessary

Also, we recommend you use [Places][places] if you want to request services in railstations or airports. But if you are not going to request in these places it is not necessary for you too

If you do not choose the generic user option and your users can change his/her data: first name, last name, phone or even gender. So, you should use [Edit profile][edit-profile]

For good feedback. Please, you should use [Vote endpoint][vote-service]. If we do not know what we're doing wrong, we won't be able to improve for you :-)


### 2.2.3 Other endpoints

If you have a solution where endusers signup, so it is possible that you want to use [Validates endpoints][validates]

We have documented: [Services][services] e.g.: to synchronize one time per day (e.g.: a taxi driver was wrong for an amount, and we can update it after finishing the service). [Get Profile][get-profile] if you want to get the data we have about a user or [Address][address] to save the favorite addresses of the users (e.g.: home, work, etc)

Also, we have about 20 endpoints undocumented more. So, if you need something, please [contact us][contact] because it is very possible that we have developed it.

<!-- Link section -->
  [aai]:  /#5-authentication-authorization-amp-impersonate
  [signup]: /#6-signup
  [validates]: /#7-validates
  [get-profile]: /#8-1-get-profile
  [edit-profile]: /#8-2-edit-profile
  [zone]: /#9-zone
  [create-service]:  /#10-1-create-service
  [edit-service]: /#10-2-edit
  [current-service]: /#10-3-current
  [services]: /#10-4-services
  [cancel-service]: /#10-5-cancel
  [vote-service]: /#10-6-vote-optional
  [places]: /#11-places
  [address]: /#12-address
  [push]: /#13-push-notifications
  [contact]: mailto:integrations@joinup.es
