# Ingestion Service

### Description
+ The ingestion service collects pedometer device updates.
+ Forward records with update data to a Kafka stream for other services to process the events.
+ The service receives device updates from either an HTTP API or an AMQP queue.
+ The service is a form of protocol adapter or mediator, as it converts events from one protocol (HTTP or AMQP) to another protocol (Kafka record streams).

+ A device update is a JSON document with the following entries:
  + The device identifier.
  + A synchronization identifier, which is a monotonically increasing long integer that the device updates for each successful synchronization.
  + The number of steps since the last synchronization.

+ Link: ![Screenshot](./ingest-service/src/main/resources/images/ingestion_service_architecture.png")

+ API:
  + /ingest: POST - Ingest a pedometer update (200: success, 500: internal error)
