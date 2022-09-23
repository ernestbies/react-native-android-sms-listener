## `react-native-android-sms-listener`

A utility that allows you to listen for incoming SMS messages (working in background).

### Example

```JS
import SmsListener from '@ernestbies/react-native-android-sms-listener'

SmsListener.addListener(message => {
  console.info(message)
})
```

The contents of `message` object will be:

```JS
{
  originatingAddress: string,
  body: string,
  timestamp: number
}
```

`SmsListener#addListener` returns a `CancellableSubscription` so if you want to stop listening for incoming SMS messages you can simply `.remove` it:

```JS
let subscription = SmsListener.addListener(...)

subscription.remove()
```

In recent versions of Android you might also have to ask for permissions READ_SMS and RECEIVE_SMS:

```JS
async function requestReadSmsPermission() {
  try {
    await PermissionsAndroid.request(
      PermissionsAndroid.PERMISSIONS.READ_SMS,
    );

    await PermissionsAndroid.request(
      PermissionsAndroid.PERMISSIONS.RECEIVE_SMS,
    );
  } catch (err) {}
}
```

### Installation

$ npm install --save @ernestbies/react-native-android-sms-listener
