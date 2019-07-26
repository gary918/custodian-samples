# Sending notifications using a webhook action
The [generic webhook action](https://cloudcustodian.io/docs/actions.html#webhook-action) can be used to send messages by providing an endpoint to a service that has the logic to deliver the message. For example, if a company already has a live service that delivers messages to an internal messaging tool they can utilize that service by using a webhook action in Custodian:

The example service endpoint may be the following post REST url: 

`https://notification_service.azurewebsites.net/api/v1/message`

And that endpoint may be expecting a request body described by the json-schema below:

```json
{
    notificationName: {type: string},
    notificationDescription: {type: string},
    subscription: {type: string},
    resource:
        {
            type: object,
            properties: 
            {
                name: {type: string},
                location: {type: string},
                id: {type: string}
            }
        }
}
```

An example Custodian policy that will deliver a message by using that endpoint could look like this:

```yaml
policies:
  - name: underutilized-virtual-machines
    description: Virtual machines that have an average CPU of less than 20% for the last week
    resource: azure.vm
    filters:
    - type: metric
      metric: Percentage CPU
      aggregation: average
      op: lt
      threshold: 20
      timeframe: 168
    actions:
      - type: webhook
        url: https://notification_service.azurewebsites.net/api/v1/message
        batch: false 
        body: >
        {
            notificationName: policy.name,
            notificationDescription: policy.description,
            subscription: account_id,
            resource: resource.
              {
                name: name,
                location: location,
                id: id
              }
          }
```