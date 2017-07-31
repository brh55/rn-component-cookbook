# Recipe Title
**react:** `^16.0.0-alpha.X` <br>
**react-native:** `^0.43.0`

## Problem
Your component wants to react to changes of the user rotationing their device to landscape or portrait mode.

## Solution
1. Set the initial orientation state of the component
```jsx
...
constructor(props) {
  super(props);
  
  this.state = {
    initialOrientation: true
   }
}
```

2. With the react-native's Dimension's event listener, track the changes of the 'window'.

> 🗒 Note   
> Since the dimensions of the application will only change during rotations, we can assume that changes are a 'rotation'

### Code Samples
Please use jsx as the language for `react-native` highlighting.

```jsx
// Use ... for condensing code samples to maintain relevancy
... 
render() {
  return (
    <View>
      <Text>Hello World</Text>
    <View>
  )
}
```

### Notes/Annotations
Include comments with the following symbol keys to include annotations/notes for readers.
```md
> [Symbol] [Type of Annotation]/s/s/s/s <-- 4 Spaces to force a line break
```
#### Symbols
- ⚠️ Warning
- ✏️ Pro-Tip    
- 🗒 Note    
- 💡 Idea    

#### Example

> ⚠️ Warning    
> You may run into issues at x, y, z.

> ✏️ Pro-Tip    
> Here is a condense way of writing x, y, z.

> 🗒 Note    
> Remember to do x, y, z.

> 💡 Idea    
> It may be possible to do x, y, z.

## Discussions
This section involves further discussion of possible issues, or an extended explanation.

## Additional Information
Include additional links for native elements used, code samples, and more.
- [Example Link 1](link)
- [Example Link 2](link)
- [Example Link 3](link)

---
**Before You Submit a PR**
1. Save your file with the following scheme: `recipe-title-MM-DD-YY.md`
2. Make sure to update the recipe index on the [`readme`](https://github.com/brh55/rn-component-cookbook/blob/master/readme.md), if there isn't a category that seems to fit properly, create a new category.
3. Delete this section
