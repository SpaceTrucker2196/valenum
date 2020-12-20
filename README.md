# valenum

example of how to use a hash map to convert strings to ints
```swift
import UIKit // needed for NSNumber
func stringToInt(string:String) -> Int? {
    var result = 0
    let valueMap = [
        "0" as Character : 0,
        "1" : 1,
        "2" : 2,
        "3" : 3,
        "4" : 4,
        "5" : 5,
        "6" : 6,
        "7" : 7,
        "8" : 8,
        "9" : 9
    ]
    
    for (index, char) in string.enumerated() {
        let exponent = string.count - index - 1
        if let value = valueMap[char] {
            //^ operator seems to have strangeness use pow here
            let number = Decimal(value) * pow(10, exponent)
            result += NSDecimalNumber(decimal: number).intValue
        } else {
            return nil
        }
    }
    
    return result
    
}
```
// convert
stringToInt(string:"49992")

// return nil if not int
stringToInt(string:"meow3993")
