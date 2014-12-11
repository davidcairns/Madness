# Recursive Descent into Madness

Madness is a Swift µframework for parsing strings in simple context-free grammars. Combine parsers from simple Swift expressions and parse away.

```swift
let digit = %("0"..."9") | %("a"..."f") | %("A"..."F")
let hex = digit+ --> { strtol(join("", $0), nil, 16) }
```


## Examples

See `Madness.playground` for some examples of parsing and building parse trees with Madness.


## Use

- **Concatenation**

	```swift
	x ++ y ++ z
	```

	parses `x` followed by `y` and produces parses as `(X, Y)`.

API documentation is in the source.


## Integration

1. Add this repository as a submodule and check out its dependencies, and/or [add it to your Cartfile](https://github.com/Carthage/Carthage/blob/master/Documentation/Artifacts.md#cartfile) if you’re using [carthage](https://github.com/Carthage/Carthage/) to manage your dependencies.
2. Drag `Madness.xcodeproj` into your project or workspace, and do the same with its dependencies (i.e. the other `.xcodeproj` files included in `Madness.xcworkspace`). NB: `Madness.xcworkspace` is for standalone development of Madness, while `Madness.xcodeproj` is for targets using Madness as a dependency.
3. Link your target against `Madness.framework` and each of the dependency frameworks.
4. Application targets should ensure that the framework gets copied into their application bundle. (Framework targets should instead require the application linking them to include Madness and its dependencies.)
