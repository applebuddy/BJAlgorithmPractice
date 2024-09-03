## Problem Solving Note

### Basic

- [커트라인](https://www.acmicpc.net/problem/25305)
  - sorting

```swift
let k = readLine()!.split(separator: " ").compactMap { Int(String($0)) }[1]
print(readLine()!.split(separator: " ").compactMap { Int(String($0)) }.sorted(by: >)[k-1])
```

- [알고리즘 수업 - 알고리즘의 수행 시간 4](https://boj.kr/24265)
  - math

```swift
let n = Int(readLine()!)! - 1
print("\(n * (n + 1) / 2)\n2")
```

- [대지](https://www.acmicpc.net/problem/9063)
  - math

```swift
let n = Int(readLine()!)!
var (minX, minY, maxX, maxY) = (10000, 10000, -10000, -10000)

(0..<n).forEach { _ in 
    let inputs = readLine()!.split(separator: " ").map(String.init).compactMap(Int.init)
    minX = minX > inputs[0] ? inputs[0] : minX
    minY = minY > inputs[1] ? inputs[1] : minY
    maxX = maxX < inputs[0] ? inputs[0] : maxX
    maxY = maxY < inputs[1] ? inputs[1] : maxY
}

print((maxX - minX) * (maxY - minY))
```

- [최댓값](https://www.acmicpc.net/problem/2566)

```swift
var max = 0
var pos: (Int, Int) = (0, 0)

(0..<9).forEach { i in
    readLine()!
        .split(separator: " ")
        .map { Int(String($0))! }
        .enumerated()
        .forEach { j, num in
            if max < num {
                max = num
                pos = (i, j)
            }
        }
}

print("\(max)\n\(pos.0+1) \(pos.1+1)")
```

- [너의 평점은](https://www.acmicpc.net/problem/25206)

```swift
extension String {
    var score: Double {
        switch self {
        case "A+": return 4.5
        case "A0": return 4.0
        case "B+": return 3.5
        case "B0": return 3.0
        case "C+": return 2.5
        case "C0": return 2.0
        case "D+": return 1.5
        case "D0": return 1.0
        default: return 0
        }
    }
}

let (count, sum) = (0..<20).reduce(into: (0, 0.0)) { result, _ in
    let input = readLine()!.split(separator: " ").map(String.init)
    let value = Double(input[1])!
    switch input[2] {
    case "P": break
    case "F":
        result.0 += Int(value)
    default: 
        result.0 += Int(value)
        result.1 += (value * input[2].score)
    }
}

print(sum / Double(count))
```