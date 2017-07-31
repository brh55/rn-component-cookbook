# Tracking Device Rotation
**react:** `^16.0.0-alpha.X` <br>
**react-native:** `^0.43.0`

## Problem
Your component needs to react to changes of the user rotationing their device to landscape or portrait mode.

## Solution
1. Set the initial orientation state of the component
```jsx
...
constructor(props) {
  super(props);
  
  this.state = {
    initialOrientation: true
  };
}
```

2. With the react-native's Dimension's event listener, we can now track changes to the 'window' and update the component internal state, resulting in a re-render for the component.

> 🗒 **Note**  
> We can assume on a real device that window changes are a "rotation", so we can update state in a "toggling" fashion.

```jsx
import { Dimensions } from 'react-native'
... 
constructor() {
  super(props);
  this.state = {
    initialOrientation: true
  };
  // Set the state opposite of current orientation
  Dimensions.addEventListener('change', window => this.setState(state => ({ initialOrientation: !state.initialOrientation }));
}
```

## Discussions
In addition, it's also possible to integrate this with Redux by simply replacing the `this.setState` with your injected prop or a dispatch action. As a reminder, if you do need the dimensions of the device, then simply use the Dimension's getter, `var {height, width} = Dimensions.get('window')`.

## Additional Information
- [Dimension](https://facebook.github.io/react-native/docs/dimensions.html)
