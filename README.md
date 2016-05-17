# SortingAlgorithm
常用算法总结，Swift编写，冒泡排序、选择排序、插入排序、快速排序等


####冒泡排序 O(N2)
    
    func bubbleSort<T: Comparable>(oArr: [T]) -> [T] {
        var arr = oArr
        for outerIndex in (1...arr.count - 1).reverse() {
            for innerIndex in 0..<outerIndex {
                if arr[innerIndex] > arr[innerIndex + 1] {
                    let temp            = arr[innerIndex]
                    arr[innerIndex]     = arr[innerIndex + 1]
                    arr[innerIndex + 1] = temp
                }
            }
        }
        return arr
    }

 
####选择排序 O(N)
    
    func selectSort<T: Comparable>(oArr: [T]) -> [T] {
        var arr = oArr
        var minIndex = 0 //记录每次遍历的最小值
        for outerIndex in 0..<arr.count {
            minIndex = outerIndex
            for innerIndex in (outerIndex + 1)..<arr.count {
                if arr[minIndex] > arr[innerIndex] {
                    minIndex = innerIndex //判断最小值，记住下标
                }
                if minIndex != outerIndex { //一个轮回结束交换
                    let temp        = arr[outerIndex]
                    arr[outerIndex] = arr[minIndex]
                    arr[minIndex]   = temp
                }
            }
        }
        return arr
    }


####插入排序 O(N2/4)
  
    func insertionSort<T: Comparable>(oArr: [T]) -> [T] {
        var arr = oArr
        for outerIndex in 1..<arr.count {
            let temp = arr[outerIndex]
            var innerIndex = outerIndex
            while innerIndex > 0 && arr[innerIndex - 1] >= temp {
                arr[innerIndex] = arr[innerIndex - 1]
                innerIndex      -= 1
            }
            arr[innerIndex] = temp
        }
        return arr
    }


####快速排序 O(N2)

    extension Array {
        var decompose : (head: Element, tail: [Element])? {
            return (count > 0) ? (self[0], Array(self[1..<count])) : nil
        }
    }
    
    func quickSort<T: Comparable>(oArr: [T]) -> [T] {
        let arr = oArr
        if let (pivot, rest) = arr.decompose {
            let lesser  = rest.filter { $0 < pivot }
            let greater = rest.filter { $0 >= pivot }
            return quickSort(lesser) + [pivot] + quickSort(greater)
        } else {
            return []
        }
    }







