# Prevent declaring unused methods of component class (react/no-unused-class-component-methods)

Warns you if you have defined a method or property but it is never being used anywhere.

## Rule Details

The following patterns are considered warnings:

```jsx
class Foo extends React.Component {
  handleClick() {}
  render() {
    return null;
  }
}
```

```jsx
class Foo extends React.Component {
  foo = bar;
  render() {
    return null;
  }
}
```


```jsx
class Foo extends React.Component {
  constructor(props) {
    super(props)
    this.foo = bar;
  }
  render() {
    return null;
  }
}
```

The following patterns are **not** considered warnings:

```jsx
class Foo extends React.Component {
  foo = 0;
  bar = 1;
  // all static methods are **not** considered warnings:
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }
  static myStaticMethod() {}
  action() {}
  // all lifecycle methods are also **not** considered warnings:
  componentDidUpdate() {}
  componentDidMount() {
    this.action();
  }
  render() {
    const { bar } = this;
    return this.foo + bar;
  }
}
```
