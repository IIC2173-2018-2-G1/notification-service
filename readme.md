# Notification Service
This is the notification microservice. It will be in charge of sending notifications upon creation of a new message in a channel or adding a reaction to a message.

This microservice will work alongside OneSignal's REST API, so it should be configured to do so.


https://documentation.onesignal.com/reference

This microservice's API wont be exposed to public.

# This service should allow inbound HTTP requests on port 8086

## Admitted Requests

- New Message On Channel:
> POST /message
```javascript
{
    channel_id: integer
}
```

> Response:
```javascript
{
    Error: string (default: "")
}
```

- New Reaction to Message:
> POST /reaction
```javascript
{
    message_id: integer
}
```

> Response:
```javascript
{
    Error: string (default: "")
}
```

- New subscription:
> POST /subscription
```javascript
{
    channel_id: integer,
    user_id: integer
}
```

> Response:
```javascript
{
    Error: string (default: "")
}
```

- Delete subscription:
> DELETE /subscription
```javascript
{
    channel_id: integer,
    user_id: integer
}
```

> Response:
```javascript
{
    Error: string (default: "")
}
```

# Things to note:
- Given that OneSignal can make notification based on the tags the user makes, this could be a way of working with notifications. Just tag on which channels the user has subscribed.
- But on every new subcription, there will have to be a way of associating OneSignal's device_id to the user. This must be handled in this microservice.