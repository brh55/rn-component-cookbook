# Parent Element Dimensions

## Problem
Your component needs to make calculations based on the available space it's placed in. This can be a reoccurring problem
for things like setting the exact width and height of an image.

## Solution
1. Wrap your component with a `<View>`
```jsx
<View>
   // Component Implementation
</View>
```
2. Use the `onLayout` property which takes a function with an event parameter. This event parameter will return the width and height of the available space.
In addition, using the internal state will allow the dimensions to dynamically reflect the accurate available space.

```jsx
render() {
  const setDimensions = (event) => {
    const {width, height} = event.nativeEvent.layout;
    // We can set the state to allow for reference through the state property, and will also change
    this.setState({
      dimensions: {
        width,
        height
      }
     });
  };
  return (
    <View onLayout={setDimensions.bind(this)}>
       // Component Implementation
    </View>
  );
}
```
 
## Additional Resources
- [View Component](https://facebook.github.io/react-native/docs/view.html)
