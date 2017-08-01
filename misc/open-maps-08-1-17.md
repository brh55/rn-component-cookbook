# Deep Link Maps For A Location
**react:** `^16.alpha.X` <br>
**react-native:** `^0.43.0`

> Most likely supported for older versions of RN > (~0.34)

## Problem
Your component needs a deep link to open up Google Maps or Apple Maps for a location.

## Solution
1. Use the `linking` library provided by react-native    
   ```jsx
   import { Linking } from 'react-native';
   ```
2. The `.openURL` method can take the following URLS to open the corresponding map application:
    ```jsx
   Linking.openURL(`http://maps.apple.com/?ll=${LATITUDE},${LONGITUDE}`)
   ```
   
    - **Google/Android:**    
       - `geo:${LATITUDE},${LONGITUDE}`    
       - `http://maps.google.com/maps?q=${LATITUDE},${LONGITUDE}`
    - **iOS:**    
       - `http://maps.apple.com/?ll=${LATITUDE},${LONGITUDE}`

> ✏️ **Pro-Tip**    
> Use `Platform.OS` *(=== 'ios' || 'android')* to allow cross-platform linking

> 🗒 **Note**    
> You can also pass in the `z` query param to set desired zoom levels    
> **IE:** `http://maps.apple.com/?ll=37.484847,-122.148386&z=15`

## Additional Information
- [Linking](https://facebook.github.io/react-native/docs/linking.html)
- [Platform](https://facebook.github.io/react-native/docs/platform-specific-code.html)
- [react-native-open-maps](https://github.com/brh55/react-native-open-maps) - A wrapper lib that performs this logic
