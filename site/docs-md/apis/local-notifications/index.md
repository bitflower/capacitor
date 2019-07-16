---
title: Local Notifications
description: Local Notifications API
url: /docs/apis/local-Notifications
contributors:
  - mlynch
  - jcesarmobile
---

<plugin-platforms platforms="pwa,ios,android,electron"></plugin-platforms>

# Local Notifications

The Local Notification API provides a way to schedule "local" notifications - notifications that are scheduled and delivered on the device as opposed to "push" notifications sent from a server.

Local Notifications are great for reminding the user about a change in the app since they last visited, providing reminder features, and delivering offline information with the app being in the foreground.

<plugin-api index="true" name="local-notifications"></plugin-api>

## Example

```typescript
import { Plugins } from '@capacitor/core';
const { LocalNotifications } = Plugins;

LocalNotifications.schedule({
  notifications: [
    {
      title: "Title",
      body: "Body",
      id: 1,
      schedule: { at: new Date(Date.now() + 1000 * 5) },
      sound: null,
      attachments: null,
      actionTypeId: "",
      extra: null
    }
  ]
});
```

## Scheduling Options

```typescript
LocalNotifications.schedule({
  notifications: [
    {
      ...
      schedule: { 
         at: new Date(Date.now() + 1000 * 120)  // Triggers a notification once in 2 minutes
      },
      schedule: { 
         at: new Date(Date.now() + 1000 * 120), // Triggers a notification once in 2 minutes
         repeats: true                          // and repeats every 2 minutes
      },
      schedule: { 
         on: {                                  // Triggers a series of repeated notifications from a certain moment of time on. No option to turn off repetition.
            year?
            month?
            day?
            hour?
            minute?
         }
      },
      schedule: { 
         every: 'month'                         // Triggers a series of repeated notifications every 'year'|'month'|'two-weeks'|'week'|'day'|'hour'|'minute'|'second' starting from current date & time. No option to turn off repetition.
      },
    }
  ]
});
```

## API

<plugin-api name="local-notifications"></plugin-api>
