### Trigger on Queued Records

* Fluxx Queues are created in the Fluxx Admin panel => Card Documents => [[ model type ]] => API Alerts. [_see Fluxx documentation for API Queue_](https://fluxxdev.atlassian.net/servicedesk/customer/portal/1/article/1795884009)
* In a nutshell, the API Queue system allows you to create a filter. Any time a record matches a Queue filter, the record is added to that queue. Zapier will poll the queue at regular intervals, and will loop through the list of records returned. You can also set up the Queue to add records that enter a particular state, or where a specific field is changed.
* API queues are identified by the Queue UUID, shown in the Fluxx Admin panel.
* Any fields selected from the Extra Fields selector in the Fluxx Admin panel are made available in subsequent Zapier steps.
* Records processed the the API queue are _not_ subject to de-duping in Zapier. i.e. Zapier will process the same record multiple times if it is added to multiple queues, or to the same queue on multiple occasions. Tech note: This is achieved by giving Zapier a derived key for each record, based on the record ID and the current time, rather than the record id alone.
