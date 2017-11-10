# Swappable/Injectable Component
> **By:** Brandon Him - *[brh55](https://github.com/brh55)*   
> **Contributors:** *N/A*

**react:** `*` <br>
**react-native:** `*`

## Problem
This problem rised mainly from the issue of developing open-source components, where vast users have different preferred components.

The result is the typical "duck" problem -- numerous types and variations available, but they are simply ducks (🦆🦆) at the end of the day.

The only obvious caveat is ensuring that the third-party component utilizes the same interface, otherwise you'll have unexpected behaviors.

## Solution
1. Create a conditional to determine if a component has been injected. In this example, we shall assume that a custom image component will be passed through a `customComponent` prop
```jsx
// ... omit standard code above
render() {
  const imageProps = {
    uri: this.props.uri
  };

  if (this.props.customComponent) {
    const CustomImageComponent = this.props.customComponent;  
    // Assign it to a variable to make it easier for referencing
    return (
      <CustomImageComponent {...imageProps}>
    );
  }
  // Image becomes the default rendered 
  return (
    <Image {...imageProps}/>
  )
}
```

2. In order to handle additional custom properties, we will assume that we are using `customComponentProps` to pass along properties.

```jsx
// ... omit standard code above
render() {
  const imageProps = {
    uri: this.props.uri
  };

  if (this.props.customComponent) {
    const CustomImageComponent = this.props.customComponent;  
    const customProps = this.props.customComponentProps;
    // Assign it to a variable to make it easier for referencing, 
    // Note: Ensure the defaultProps are assigned first, before customComponentProps
    return (
      <CustomImageComponent
      {...imageProps}
      {...customComponentProps}>
    );
  }

  return (
    <Image {...imageProps}/>
  )
}
```

3. Now your component should render a default component, but also accept a custom component as well as props.

```jsx
<YourComponent
  customComponent={AwesomeImage}
  customComponentProps={AwesomeImageProps}
/>
```

> ✏️ **Pro-Tip**    
> Use `prop-types` to provide some basic type-checking for your component
> `.func` for the third-party component and `.object` for the properties
>
> ```jsx
> YourComponent.propTypes = {
> 	customComponent: PropTypes.func,
>   customComponentProps: PropTypes.object
> }
> ```

## Discussions

Feel free to use [`react-native-injectable-component`](https://github.com/brh55/react-native-injectable-component). The module can easily be plugged into an existing project. The module also accounts for any nested children, checks for accurate types, as well as ensure default properties are assigned prior to custom component props.

**Sample usage**
```jsx
<Injector
  defaultComponent={Image}
  defaultProps={imageProps}
  injectant={props.customComponent}
  injectantProps={props.customComponentProps}
/>
```

## Additional Information
- [prop-types](https://github.com/facebook/prop-types) - Runtime type checking for React props and similar objects
