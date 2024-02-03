## Big O Notation
Is about how the running time of an algorithm increases with the size of the input.
It is a measure of the performances of the algorithm based on the input.

## Swift Stride
Lets you move from one value to another using any increment and even lets you specify whether the upper bound is exclusive or inclusive. <br>
`stride(from:to:by:)` exclude upper bound
```
for i in stride(from: 0, to: 10, by: 1) {
  print(i) // prints from 0 to 9
}
```
`stride(from:through:by:)`  include upper bound
```
for i in stride(from: 0, through: 10, by: 1) {
  print(i) //prints 0 to 10
}
```


## Buble Sort  / Time complexity: O(n²)
It is always slow. In the best or worst case. <br>
It is the simplest one that repeatedly steps through the input list element by element, comparing the current element with the one after it.
```
func bubble(_ input: [Int]) -> [Int] {
    var result = input
    for i in 0..<result.count {
        for j in 0...i {
            if result[i] < result[j] {
                let temp = result[i]
                result[i] = result[j]
                result[j] = temp
            }
        }
    }
    return result
}
```

## Selection Sort / Time complexity: O(n²)
It will search for the smallest item, when finishes the iteration it will replace the smallest item founded with the current minimum item. In the next iteration of the algorithm the current minimum item will be moved to the next item in the array and the search for the smallest item begins again.
```
func selection(_ input: [Int]) -> [Int] {
    var result = input
    for i in 0..<result.count {
        for j in i+1..<result.count {
            if result[i] > result[j] {
                let temp = result[i]
                result[i] = result[j]
                result[j] = temp
            }
        }
    }
    return result
}
```

## Insertion Sort
Is a sort algorithm that card players like to use to sort the cards they hold. It is pretty straight foward.
Using this algorithm you are looking at the next element, and you are trying to find a place for it by comparing it to the previous element, you will switch the two elements.
```
func insertionSort<T: Comparable>(_ input: [T]) -> [T] {
    var result = input
    let length = result.count
    for i in 1..<length {
        for j in stride(from: i, to: 0, by: -1) {
            if result[j] < result[j - 1] {
                var temp = result[j - 1]
                result[j - 1] = result[j]
                result[j] = temp
            }
        }
    }
    return result
}
```
## Missing sequence number
```
public func solution(_ A : inout [Int]) -> Int {
    var missingNumber = A.first ?? 0
    let newArray = Array(1...A.count + 1)
    for i in newArray {
        for element in A {
            if i == element {
                break
            } else {
                missingNumber = i
            }
        }
    }
    return missingNumber
}

```

## Prefix Sum
Given query values P, Q to create a range and find the lowest value.
```
public func solution(_ S : inout String, _ P : inout [Int], _ Q : inout [Int]) -> [Int] {
     let stringArray = Array(S)
    var genoms: [[Int]] = Array(repeating: Array(repeating: 0, count: S.count + 1), count: 3)
    let hash: [String: Int] = [
        "A": 1,
        "C": 2,
        "G": 3,
        "T": 4
    ]

    for (index, element) in stringArray.enumerated() {
        var a = 0
        var c = 0
        var g = 0
        if element == "A" {
            a = 1
        }
        if element == "C" {
            c = 1
        }
        if element == "G" {
            g = 1
        }
        genoms[0][index + 1] = genoms[0][index] + a
        genoms[1][index + 1] = genoms[1][index] + c
        genoms[2][index + 1] = genoms[2][index] + g
    }
         
    var result: [Int] = []

    for index in 0..<P.count {
        let fromIndex = P[index]
        let toIndex = Q[index]

        if stringArray[fromIndex] == "A" {
            result.append(1)
            continue
        } else if stringArray[toIndex] == "A" {
            result.append(1)
            continue
        } else if toIndex == fromIndex {
            let key = "\(stringArray[toIndex])"
            let value = hash[key]
            result.append(value!)
            continue
        }

        if genoms[0][toIndex + 1] > genoms[0][fromIndex] {
            result.append(1)
        } else if genoms[1][toIndex + 1] > genoms[1][fromIndex] {
            result.append(2)
        } else if genoms[2][toIndex + 1] > genoms[2][fromIndex] {
            result.append(3)
        } else {
            result.append(4)
        }
    }

    return result
}
```
