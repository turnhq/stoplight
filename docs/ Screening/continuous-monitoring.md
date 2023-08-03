# Continuous Monitoring

## Continuous Criminal Monitoring
Turn’s Continuous Criminal Monitoring service will help our customers to keep a close eye on any criminal activity with active employees.

Upon enrollment, Continuous Criminal Monitoring will deliver fresh background check results including the alerted county due to arrest events that occur with monitored individuals.

1.  Monitor all arresting events at State/County Booking Facilities.
2.  Run a background check at the county criminal level on the alerted individuals, and
3.  Deliver background check results and adjudication determinations (if applicable) based on those results.

This feature allows users to request the following actions via API:

\t\- Enroll: Add to the Continuous Criminal Monitoring service.
\t\- Unenroll: Remove from the Continuous Criminal Monitoring service.
\t\- Query Enrollees: Query our system for currently enrolled individuals. 

In the event a monitored individual is flagged by Turn for an arrest, Turn will wait 7 business days (this is the recommended lead time for data to be discoverable at the courthouse level) to conduct a criminal recheck at the corresponding County Courthouse.

- IF a corresponding charge and disposition IS discovered, Turn will send the recheck results via status update webhooks with a continuous monitoring tag.
- IF a corresponding charge and disposition IS NOT discovered, Turn will send the recheck results to the partner via status update webhooks WITHOUT a continuous monitoring tag and run a subsequent background check 30 days later.

Notes:

<u>CA Exclusion</u>: Because California is not an evergreen state, Turn will need to collect additional consent from the monitored individual in the event of a monitoring hit in order to run the background check.

<u>No Alerts for Booking Events</u>: Due to FCRA regulations, Turn can only notify partners of a booking event if a corresponding charge was found at the courthouse. Turn cannot notify partners solely upon obtaining an arrest record.
