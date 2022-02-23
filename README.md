## Big O Notation
Is about how the running time of an algorithm increases with the size of the input.
It is a measure of the performances of the algorithm based on the input.

## Swift Stride
Lets you move from one value to another using any increment and even lets you specify whether the upper bound is exclusive or inclusive.
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
Just educational. It is always slow. In the best or worst case.
```
extension Array where Element: Comparable {
  func bubbleSort(by areInIncreasingOrder: ((Element, Element)) -
}
```

## Selection Sort / Time complexity: O(n²)
It will search for the smallest item, when finishes the iteration it will replace the smallest item founded with the current minimum item. In the next iteration of the algorithm the current minimum item will be moved to the next item in the array and the search for the smallest item begins again.
```
func selectionSort(_ input: [Int]) -> [Int] {
    var result = input
    let length = result.count

    for i in 0..<length {
        var minIndex = i
        for j in i+1..<length {
            if result[j] < result[minIndex] {
                minIndex = j
            }
        }
        let temp = result[i]
        result[i] = result[minIndex]
        result[minIndex] = temp
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
  return result
}
```
