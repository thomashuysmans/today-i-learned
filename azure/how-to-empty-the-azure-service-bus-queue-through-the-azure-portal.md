## How to empty the Azure Service Bus Queue through the Azure Portal

There is no obvious way to empty the Azure Service Bus queue using the Azure Portal. The trick is to change the Message time to Live (TTL) to the absolute minimum. This setting is 14 days by default, but you can change it to 5 seconds. 

How to change the Message time to Live:

1. Go to the overview page of your Azure Service Bus queue. There is an overview of the different settings. 
2. Look for Message time to live and click on the change link. 
3. Change the value to 5 seconds. 
4. Wait a minute or two. This depends on how big your queue is
5. The queue will empty

