# OptionSet

Using OptionSet.

```swift 
struct ShippingOptions: OptionSet {
    let rawValue: Int

    static let nextDay = ShippingOptions(rawValue: 1 << 0)
    static let secondDay = ShippingOptions(rawValue: 1 << 1)
    static let priority = ShippingOptions(rawValue: 1 << 2)
    static let standard = ShippingOptions(rawValue: 1 << 3)

    static let express: ShippingOptions = [.nextDay, .secondDay]
    static let all: ShippingOptions = [.express, .priority, .standard]
}


// test
let purchasePrice = 80

var freeOptions: ShippingOptions = []

if purchasePrice > 50 {
    freeOptions = [.priority]
}

if freeOptions.contains(.priority) {
    print("You've earned priority shipping.")
} else {
    print("Add more to your cart to earn free priority shipping.")
}
```

## Resources 

* [SwiftDoc.org](https://swiftdoc.org/v3.0/protocol/optionset/)
