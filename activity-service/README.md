# Activity Service
![Screenshot](https://github.com/jackson0726/10k-steps-challenge/blob/main/activity-service/src/main/resources/images/activity-service-arc.png)

### Description
+ The activity service keeps track of step-activity updates sent by the pedometers.
+ The service stores events to a PostgreSQL database and offers an HTTP API to gather some statistics, such as daily, monthly, and total step counts for a given device.
+ Updates are received from a Kakfa topic, which is fed by the ingestion service.
+ The activity service also publishes events with the number of steps for a device on the current day.
+ This way, other services can subscribe to the corresponding Kafka topic and be notified rather than having to regularly poll the activity service for updates.

+ API:
  + /<device_id>/total: GET - Total step count for a device (200: success, 404: the device does not exist, 500: internal error).
  + /<device_id>/<year_>/<month_>: GET - Step count for a device in a particular month (200: success, 404: the device does not exist, 500: internal error).
  + /<device_id>/<year_>/<month_>/<day_>: GET - Step count for a device on a particular day (200: success, 404: the device does not exist, 500: internal error).
  + /ranking-last-24-hours: GET - Ranking of the devices in decreasing number of steps over the last 24 hours (200: success, 500: internal error).
