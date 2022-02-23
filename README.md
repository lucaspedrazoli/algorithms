## Big O Notation
Is about how the running time of an algorithm increases with the size of the input.
It is a measure of the performances of the algorithm based on the input.
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
