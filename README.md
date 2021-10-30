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

// create unique options as static properties of your custom type
// using unique powers of two (1, 2, 4, 8, 16, and so forth)
// for each individual property's raw value so that each property
// can be represented by a single bit of the type's raw value.

// shifting bits to the left
1 << 0 // 0001 => 1
1 << 1 // 0010 => 2
1 << 2 // 0100 => 4
1 << 3 // 1000 => 8
1 << 4 // 0000_0000 => 16
1 << 5 // 0010_0000 => 32
```

## Resources 

* [Apple Documentation](https://developer.apple.com/documentation/swift/optionset)
