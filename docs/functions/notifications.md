# Notifications

Notifications received due to contact with someone with COVID-19 as referred to
as [contact alerts](./docs/functions/contact-alerts.md). 

## Announcement notifications

From time to time, the Ministry of Health may decide to send an announcement
to all users of NZ COVID Tracer, for example information about alert levels.

1. A push notification is sent to all subscribers to the `announcements` topic.
2. An announcement component is shown to all users on the dashboard. 
3. An indicator is shown to all users on the dashboard menu icon.

Sometimes, the dashboard announcement component may be shown without
sending a push notification, for example where a civil defence
alert has been issued and an additional notification is not required. 

The dashboard announcement is distributed through the settings endpoint
and configured through Parameter Store.

Users are automatically subscribed to the `announcements` topic upon
downloading or upgrading to a version of the app after v4.1.0. They
may unsubscribe from this topic by going to the Notification Preferences
screen from the My Data tab. Users who are unsubscribed will still
see announcements on the dashboard.

## Diary reminder notifications

As of v6.0.0, the app schedules local reminder notifications to be 
received a set amount of time after a diary entry was added by scanning a QR code,
tapping an NFC tag, or adding a diary entry manually.
These are rescheduled each time that a new diary entry is added,
so that the user will be notified when the set time has elapsed without another
diary entry being added. 
When a scheduled reminder notification is received, components are shown on
the dashboard and on the diary screen. These contain configured text and
a link to manage notifications.

The frequency and text of these notifications are configured by the Ministry
of Health. The initial settings are for a first notification to be scheduled
for 7 days in the future and a second notification for 14 days in the future.

A user may opt out from these notifications by going to the Notification Preferences
screen from the My Data tab. This will remove all scheduled notifications 
and prevent new ones from being scheduled.
