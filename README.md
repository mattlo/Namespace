# Namespace Simple
A simple method that generates N amount of nested objects to create a namespace-like construct.

## Install

Clone the repository and include directly into your project. You can also use bower and install as a dependency:

```
bower install namespace-simple
```

## Usage

Declaring on top of a file in a practical scenario:

```
// file1.js
NS('foo.bar.baz');
foo.bar.baz.Object = {name: "Matt"};

// file2.js
NS('foo.bar.baz');
foo.bar.baz.AnotherObject = {name: foo.bar.baz.Object.name + " Lo"};

// some other file dot js that has file1.js and file2.js loaded respectively
foo.bar.baz.Object; // {name: "Matt"}
foo.bar.baz.AnotherObject; // {name: "Matt Lo"}
```

Chained:

```
NS('Constants.Configs').App = {
	NAME: "Namespaced!"
};

Constants.Configs.App.NAME; // "Namespaced!"
```

## Notes

Namespaces won't be created on existing objects that were not generated from `NS`.

```
var foo = {};

NS('foo.bar.baz'); // Error: Non Namespace Object exists, cannot create namespace.
```

Namespaces are instantiated from an `NS` internal `Namespace` object that faciliates checking if a namespace can be created or not.

```
NS('foo');

foo; // Namespace {}

foo.bar = {};

NS('foo.bar.baz'); // Error: Non Namespace Object exists, cannot create namespace.
```

## License

Apache License Copyright 2014 Matt Lo