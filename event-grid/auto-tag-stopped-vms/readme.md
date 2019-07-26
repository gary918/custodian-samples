Overview
========
Cloud Custodian's Azure Event Grid mode creates a subscription listening to every events written to Activity Log in Subscription level. 
Whenever an event was written to Activity Log, the event will be picked up by subscription and sent to a Storage Queue. 
A Azure Function then pick up events fromt he queue and process them.

>! Note - Because Event Grid Mode uses Activity Log, only an Activity log event will trigger Event Grid policy