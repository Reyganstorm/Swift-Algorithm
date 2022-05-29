# Примечание об обозначении О-нотация (Big-O)

Полезно знать, насколько быстр алгоритм и сколько места ему нужно. Это позволяет выбрать правильный алгоритм для работы.

Обозначение Big-O дает приблизительное представление о времени работы алгоритма и объеме памяти, который он использует. Когда кто-то говорит: «Этот алгоритм в худшем случае имеет время выполнения  **O(n^2)** и использует **O(n)** пространства», они имеют в виду, что он довольно медленный, но не требует большого количества дополнительных памяти.

Выяснение Big-O алгоритма обычно выполняется с помощью математического анализа. Мы опускаем здесь математику, но полезно знать, что означают разные значения, поэтому вот удобная таблица. **n** относится к количеству элементов данных, которые вы обрабатываете. Например, при сортировке массива из 100 элементов **n = 100**.

О-нотация | Название | Описание
------| ---- | -----------
**O(1)** | константный | **Это лучший вариант.** Алгоритм всегда занимает одинаковое количество времени, независимо от объема данных. Пример: поиск элемента массива по его индексу.
**O(log n)** | логарифмический | **Отлично.** Подобные алгоритмы уменьшают вдвое объем данных с каждой итерацией. Если у вас есть 100 элементов, для поиска ответа требуется около 7 шагов. Для 1000 элементов требуется 10 шагов. А для 1 000 000 элементов требуется всего 20 шагов. Это очень быстро даже для больших объемов данных. Пример: бинарный поиск.
**O(n)** | линейный | **Хорошая производительность.** Если у вас есть 100 элементов, это выполняет 100 единиц работы. Удвоение количества элементов приводит к тому, что алгоритм занимает ровно вдвое больше времени (200 единиц работы). Пример: последовательный поиск.
**O(n log n)** | "линеарифмический" | **Достойная производительность.** Это немного хуже, чем линейное, но не так уж плохо. Пример: самые быстрые алгоритмы сортировки общего назначения.
**O(n^2)** | квадратичный | **Довольно медленно.** Если у вас есть 100 элементов, это означает 100^2 = 10 000 единиц работы. Удвоение количества элементов делает его в четыре раза медленнее (потому что 2 в квадрате равно 4). Пример: алгоритмы, использующие вложенные циклы, такие как сортировка вставками.
**O(n^3)** | кубический | **Низкая производительность.** Если у вас есть 100 элементов, 100^3 = 1 000 000 единиц работы. Удвоение размера ввода делает его в восемь раз медленнее. Пример: умножение матриц.
**O(2^n)** | экспоненциальный | **Очень низкая производительность.** Вы хотите избежать таких алгоритмов, но иногда у вас нет выбора. Добавление всего одного бита ко входу удваивает время работы. Пример: задача коммивояжера.
**O(n!)** | факториал | **Невыносимо медленно.** На то, чтобы что-то сделать, уходит буквально миллион лет.


Below are some examples for each category of performance:

**O(1)**

  The most common example with O(1) complexity is accessing an array index.

  ```swift
  let value = array[5]
  ```

  Another example of O(1) is pushing and popping from Stack.


**O(log n)**

  ```swift
  var j = 1
  while j < n {
    // do constant time stuff
    j *= 2
  }
  ```  

  Instead of simply incrementing, 'j' is increased by 2 times itself in each run.

  Binary Search Algorithm is an example of O(log n) complexity.


**O(n)**

  ```swift
  for i in stride(from: 0, to: n, by: 1) {
    print(array[i])
  }
  ```

  Array Traversal and Linear Search are examples of O(n) complexity.  


**O(n log n)**

  ```swift
  for i in stride(from: 0, to: n, by: 1) {
  var j = 1
    while j < n {
      j *= 2
      // do constant time stuff
    }
  }
  ```

  OR

  ```swift
  for i in stride(from: 0, to: n, by: 1) {
    func index(after i: Int) -> Int? { // multiplies `i` by 2 until `i` >= `n`
      return i < n ? i * 2 : nil
    }
    for j in sequence(first: 1, next: index(after:)) {
      // do constant time stuff
    }
  }
  ```

  Merge Sort and Heap Sort are examples of O(n log n) complexity.  


**O(n^2)**

  ```swift
  for i  in stride(from: 0, to: n, by: 1) {
    for j in stride(from: 1, to: n, by: 1) {
      // do constant time stuff
    }
  }
  ```

  Traversing a simple 2-D array and Bubble Sort are examples of O(n^2) complexity.


**O(n^3)**

  ```swift
  for i in stride(from: 0, to: n, by: 1) {
    for j in stride(from: 1, to: n, by: 1) {
      for k in stride(from: 1, to: n, by: 1) {
        // do constant time stuff
      }
    }
  }
  ```  

**O(2^n)**

  Algorithms with running time O(2^N) are often recursive algorithms that solve a problem of size N by recursively solving two smaller problems of size N-1.
  The following example prints all the moves necessary to solve the famous "Towers of Hanoi" problem for N disks.

  ```swift
  func solveHanoi(n: Int, from: String, to: String, spare: String) {
    guard n >= 1 else { return }
    if n > 1 {
      solveHanoi(n: n - 1, from: from, to: spare, spare: to)
    } else {
      solveHanoi(n: n - 1, from: spare, to: to, spare: from)
    }
  }
  ```


**O(n!)**

  The most trivial example of function that takes O(n!) time is given below.

  ```swift
  func nFacFunc(n: Int) {
    for i in stride(from: 0, to: n, by: 1) {
      nFactFunc(n - 1)
    }
  }
  ```

Often you don't need math to figure out what the Big-O of an algorithm is but you can simply use your intuition. If your code uses a single loop that looks at all **n** elements of your input, the algorithm is **O(n)**. If the code has two nested loops, it is **O(n^2)**. Three nested loops gives **O(n^3)**, and so on.

Note that Big-O notation is an estimate and is only really useful for large values of **n**. For example, the worst-case running time for the [insertion sort](Insertion%20Sort/) algorithm is **O(n^2)**. In theory that is worse than the running time for [merge sort](Merge%20Sort/), which is **O(n log n)**. But for small amounts of data, insertion sort is actually faster, especially if the array is partially sorted already!

If you find this confusing, don't let this Big-O stuff bother you too much. It's mostly useful when comparing two algorithms to figure out which one is better. But in the end you still want to test in practice which one really is the best. And if the amount of data is relatively small, then even a slow algorithm will be fast enough for 
