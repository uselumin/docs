---
sidebar_position: 4
---

# Custom Events

Custom events allow you to define your own KPIs. Each custom event you send will be counted and displayed in your dashboard.

To send a custom event from your app, use the `.trackCustomEvent()` method on the `Lumin` instance. Here's an example to track a the click of a button:

```jsx
    <Button
        title="Track Custom Event"
        onPress={() => {
          lumin.trackCustomEvent('CUSTOM_EVENT_NAME');
        }}
    />
```

## Sharing One Lumin Instace Across Your App

When you're tracking custom events, you likely won't do so only from your `App.js`. So we recommend to pull your Lumin setup code out of `App.js` into its own module. Here's an example of how you can do that:

```javascript title="lumin.js"
import { Lumin } from "@uselumin/react-native";

const lumin = null;
if (process.env.ENVIRONMENT === "production") {
    lumin = new Lumin("<Token of your PROD Lumin app>");
} else 
if (process.env.ENVIRONMENT === "development") {
    lumin = new Lumin("<Token of your DEV Lumin app>");
} else
if // ...

lumin.init();

export lumin;
```