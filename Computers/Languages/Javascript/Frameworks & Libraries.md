---
created: 2024-02-07 10:35:40Z
---
## Typescript
- static typing: annotation
	- variables, function parameters, return values, & objects
	- Types can be inferred
- Interfaces  / Type Aliases
- Generics
- Utility types
	- `Partial<T>`, `Pick<T>`
- Options
	- `strictNullChecks`
	- `noImplicitAny`
	- `strictPropertyInitialization`

## Node.js
- `require` instead of `import`
```js
// imports 'createServer()' from Standard Library Module 'http'
const { createServer } = require('node:http');
```

# React.js
- Component architecture allows easier development of  HTML/CSS/JS web application user interfaces
## React Native
- Used to build applications which can be run on both iOS and Android devices
### Shared Characteristics
- share core React.js library (component-based architecture) & Javascript APIs
- use virtual DOMs to render
- use Chrome DevTools for debugging
- Developed in Meta
	- React: Jordan Walke
	- React Native: Hackathon

# Node.js

# Flutter
- Uses [Dart](../../Computers/Javascript/Dart.md) programming language

# Comparison of Mobile App Frameworks

The following images depict the functional differences^[image taken from [this](https://blog.codemagic.io/what-is-flutter-benefits-and-limitations/) webpage]
## Native Environment


![Native](../../_resources/native.png)


## React Native
![React Native](../../_resources/react_native.png)
## Flutter
![Flutter](../../_resources/flutter.png)

# Dart
## Used in Flutter
Look [here](../../Computers/Javascript/Frameworks%20&%20Libraries.md#flutter)

## Points of Interest
- Similar to Javascript
	- Except uses AOT and JIT compilation
	- Approximately twice as fast
- Single object paradigm (classes)
- Open-Source
- Garbage Collection
- Widget-based architecture
- Richer component (widget) library than [React Native](../../Computers/Javascript/Frameworks%20&%20Libraries.md#react-native) (more of a framework)
- Developed in Google around 2015
- For both iOS and Android apps simultaneously