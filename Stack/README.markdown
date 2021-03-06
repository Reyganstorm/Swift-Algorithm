# Стек

> This topic has been tutorialized [here](https://www.raywenderlich.com/149213/swift-algorithm-club-swift-stack-data-structure)

Стек похож на массив, но с ограниченной функциональностью. Вы можете только *добавить* 'push', чтобы добавить новый элемент на вершину стека, *извлечь* 'pop', чтобы удалить элемент сверху, и *заглянуть* 'peek' в верхний элемент, не извлекая его.

Почему вы хотите это сделать? Ну, во многих алгоритмах вы хотите в какой-то момент добавить объекты во временный список, а затем снова извлечь их из этого списка позже. Часто порядок, в котором вы добавляете и удаляете эти объекты, имеет значение.

Стек дает вам LIFO (англ. last in, first out, «последним пришёл — первым ушёл»). Элемент, который вы добавили последним, извлечется первым со следующим всплывающим окном. (Очень похожая структура данных, [queue](../Queue/), представляет собой FIFO - «первым пришел – первым обслужен».)

Например, давайте добавим число в стек: 

```swift
stack.push(10)
```

Стек теперь `[ 10 ]`. Добавим следующее число:

```swift
stack.push(3)
```

Стек теперь `[ 10, 3 ]`. Добавим еще одно число:

```swift
stack.push(57)
```

Стек теперь `[ 10, 3, 57 ]`. Теперь давайте извлечем верхнее число из стека:

```swift
stack.pop()
```

Оно вернуло `57`, потому что это было самое последнее число, которое мы добавили. Стек `[ 10, 3 ]` снова.

```swift
stack.pop()
```

Оно вернуло `3`, и так далее. Если стек будет пустой, *pop* вернет `nil` или в некоторых реализациях выдает сообщение об ошибке ("stack underflow").

Стек легко создать в Swift. Это просто обертка вокруг массива, которая позволяет вам помещать, извлекать и просматривать верхний элемент стека:

```swift
public struct Stack<T> {
  fileprivate var array = [T]()
  
  public var isEmpty: Bool {
    return array.isEmpty
  }
  
  public var count: Int {
    return array.count
  }
  
  public mutating func push(_ element: T) {
    array.append(element)
  }
  
  public mutating func pop() -> T? {
    return array.popLast()
  }
  
  public var top: T? {
    return array.last
  }
}
```

Обратите внимание, что 'push' помещает новый элемент в конец массива, а не в начало. Вставка в начало массива является дорогостоящей операцией **O(n)**, потому что она требует смещения всех существующих элементов массива в памяти. Добавление в конце **O(1)**; это всегда занимает одинаковое количество времени, независимо от размера массива.


Забавный факт о стеках: каждый раз, когда вы вызываете функцию или метод, CPU помещает адрес возврата в стек. Когда функция завершается, CPU использует этот адрес возврата для возврата к вызывающей программе. Вот почему, если вы вызываете слишком много функций — например, в рекурсивной функции, которая никогда не завершается — вы получаете так называемое «stack overflow», поскольку стек CPU исчерпан.

*Written for Swift Algorithm Club by Matthijs Hollemans и перевел Руслан*
