- [Алгоритмы](#алгоритмы)
	- [Нотация «большое О»](#нотация-большое-о)
	- [Последовательный поиск](последовательный-поиск)
	- [Бинарный поиск](#бинарный-поиск)
	- [Последовательный поиск](#последовательный-поиск)
	- [Сортировка вставками](#сортировка-вставками)
	- [How to merge two sorted arrays into a sorted array](#merge-arrays)
	- [Рекурсивная функция](#рекурсивная-функция)

<a name="алгоритмы"></a>
# Алгоритмы
<a name="нотация-большое-о"></a>
## Нотация «большое О»
Performance is usually described with the Big O Notation. It defines the limiting behavior of a function and is often used to characterize algorithms on their performance. O defines the upper bound of the growth rate of the function. To see just how big the difference is, see commonly used O notations and the number of operations needed.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/big_o_complexity.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/algo_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/algo_2.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/algo_3.png">

For example, if you sort an array with 50 elements, and your sorting algorithm has a complexity of `O(n^2)`, there will be 2,500 operations necessary to complete the task. Furthermore, there’s also overhead in internal management and calling that method - so it’s 2,500 operations times constant. `O(1)` is the ideal complexity, meaning constant time. Good sorting algorithms usually need `O(n log n)` time.

<a name="Последовательный поиск"></a>
## Последовательный поиск
_linear search_

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/linear_search.gif">
Для неупорядоченного массива – перебор всех элементов, пока либо не найдется элемент, либо не закончится массив.

```c
//O(n)
int linearSearch(int array[], int size, int x) {
  for (int i = 0; i < size; i++) {
    if (x == array[i]) {
      return x;
    }
  }
  return -1;
}

//O(n)
int linearSearchMax(int array[], int size) {
  int max = array[0];
  for (int i = 0; i < size; i++) {
    if (array[i] >= max) {
      max = array[i];
    }
  }
  return max;
}
```

<a name="бинарный-поиск"></a>
## Бинарный поиск
_binary search, half-interval search, logarithmic search, binary chop_

`log(n), отсортированный массив`

Алгоритм двоичного поиска похож на то, как мы ищем слово в словаре. Открываем словарь посередине, смотрим в какой из половин будет нужное нам слово. Допустим, в первой. Открываем первую часть посередине, продолжаем половинить, пока не найдем  нужное слово. С массивами так: есть упорядоченный массив, берем число из середины массива, сравниваем с искомым. Если оно оказалось больше, значит искомое число в первой половине массива, если меньше — во второй. Продолжаем делить оставшуюся половину, когда находим нужное число возвращаем его индекс, если не находим возвращаем `null`.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/binary_search.gif">
```c
int binarySearch(int array[], int size, int x) {
  int first = 0; // Первый элемент в массиве
  int last = size - 1; // Последний элемент в массиве
  if (x < array[first] || array[last] < x) {
    // x лежит вне заданного массива
    return -1;
    printf("-1");
  } else {
    while (first < last) {
      int mid = (first + last) / 2;
      if (x < array[mid]) {
        last = mid - 1;
      } else {
        first = mid;
      }
    }
    if (array[last] == x) {
      // Искомый элемент найден. last - искомый индекс
      return x;
      printf("%i", x);
    } else {
      // Искомый элемент не найден.
      return -1;
      printf("-1");
    }
  }
}
```
`NSArray` has come with built-in binary search since iOS 4 / Snow Leopard:
```objectivec
typedef NS_OPTIONS(NSUInteger, NSBinarySearchingOptions) {
  NSBinarySearchingFirstEqual     = (1UL << 8),
  NSBinarySearchingLastEqual      = (1UL << 9),
  NSBinarySearchingInsertionIndex = (1UL << 10),
};

- (NSUInteger)indexOfObject:(id)obj inSortedRange:(NSRange)range options:(NSBinarySearchingOptions)options usingComparator:(NSComparator)cmp;
```
Why would you want to use this? Methods like `containsObject:` and `indexOfObject:` start at index `0` and search every object until the match is found - they don’t require the array to be sorted but have a performance characteristic of `O(n)`. Binary search, on the other hand, requires the array to be sorted, but only needs `O(log n)` time. Thus, for one million entries, binary search requires, at most, 21 comparisons, while the naive linear search would require an average of 500,000 comparisons.

__Time to search for 1000 entries within 1000000 objects.__
```
Linear: 54130.38[ms].
Binary: 7.62[ms]
```
For comparison, the search for a specific index with `NSOrderedSet` took 0.23 ms - that’s more than 30 times faster, even compared to binary search. Keep in mind that sorting is expensive as well. Apple uses merge sort, which takes `O(n*log n)`, so if you just have to call `indexOfObject:` once, there’s no need for binary search.

<a name="сортировка-вставками"></a>
## Сортировка вставками
_insertion sort_

`O(n^2), частично отсортированный массив`

Суть его заключается в том что, на каждом шаге алгоритма мы берем один из элементов массива, находим позицию для вставки и вставляем. Стоит отметить что массив из 1-го элемента считается отсортированным.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/insertion_sort.gif">
*	Устойчив
*	Может сортировать массив по мере его поступления
```c
void insertionSort(int array[], int size) {
  int i, j, tmp;
  for (i = 1; i < size; i++) {
    tmp = array[i];
    for (j = i - 1; j >= 0 && array[j] > tmp; j--) {
      array[j + 1] = array[j];
    }
    array[j + 1] = tmp;
  }
}
```

<a name="сортировка-пузырьком"></a>
## Сортировка пузырьком
_bubble sort, sinking sort_

`O(n^2)`

Алгоритм состоит из повторяющихся проходов по сортируемому массиву. За каждый проход элементы последовательно сравниваются попарно и, если порядок в паре неверный, выполняется обмен элементов. Проходы по массиву повторяются `N-1` раз или до тех пор, пока на очередном проходе не окажется, что обмены больше не нужны, что означает — массив отсортирован. При каждом проходе алгоритма по внутреннему циклу, очередной наибольший элемент массива ставится на своё место в конце массива рядом с предыдущим «наибольшим элементом», а наименьший элемент перемещается на одну позицию к началу массива («всплывает» до нужной позиции как пузырёк в воде, отсюда и название алгоритма).
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/bubble_sort.gif">
* Эффективен для небольших массивов из-за сложности
```c
void bubbleSort(int array[], int size) {
  bool swapped = true;
  int i;
  for (i = 1; i < size; i++) {
    swapped = false; //this flag is to check if the array is already sorted
    int j;
    for (j = 0; j < size - i; j++) {
      if (array[j] > array[j + 1]) {
        int tmp = array[j];
        array[j] = array[j + 1];
        array[j + 1] = tmp;
        swapped = true;
      }
    }
    if (swapped == false) {
      break; //if it is sorted then stop
    }
  }
}
```

<a name="сортировка-выбором"></a>
## Сортировка выбором
_selection sort_
`O(n^2)`

На каждом шаге алгоритма мы выбираем один из элементов входных данных и вставляем его на нужную позицию в уже отсортированном списке, до тех пор, пока набор входных данных не будет исчерпан. Метод выбора очередного элемента из исходного массива произволен; может использоваться практически любой алгоритм выбора. Обычно (и с целью получения устойчивого алгоритма сортировки), элементы вставляются по порядку их появления во входном массиве. Приведенный ниже алгоритм использует именно эту стратегию выбора.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/selection_sort.gif">
Плюсы:

* эффективен на небольших наборах данных, на наборах данных до десятков элементов может оказаться лучшим;
* эффективен на наборах данных, которые уже частично отсортированы;
* это устойчивый алгоритм сортировки (не меняет порядок элементов, которые уже отсортированы);
* может сортировать список по мере его получения;
* использует `O(1)` временной памяти, включая стек.

Минусы:

* может быть и устойчивым, и неустойчивым
```c
int selectionSort(int array[], int size) {
  int i, j;
  int tmp;
  int min;
  for (i = 0; i < size - 1; i++) {
    min = i; //current minimum
    //find the global minimum
    for (j = i + 1; j < size; j++) {
      if (array[min] > array[j]) {
        min = j; // new minimum
      }
    }
    //swap array[i] and array[min]
    tmp = array[i];
    array[i] = array[min];
    array[min] = tmp;
  }
  return 0;
}
```

<a name="быстрая-сортировка"></a>
## Быстрая сортировка
_сортировка Хоара, quicksort, qsort_
`O(n*log(n)), разделяй и властвуй`

QuickSort является существенно улучшенным вариантом алгоритма сортировки с помощью прямого обмена (его варианты известны как «Пузырьковая сортировка» и «Шейкерная сортировка»), известного, в том числе, своей низкой эффективностью. Принципиальное отличие состоит в том, что в первую очередь производятся перестановки на наибольшем возможном расстоянии и после каждого прохода элементы делятся на две независимые группы. Любопытный факт: улучшение самого неэффективного прямого метода сортировки дало в результате один из наиболее эффективных улучшенных методов.
Общая идея алгоритма состоит в следующем:

1. Выбрать из массива элемент, называемый опорным. Это может быть любой из элементов массива.
2. Сравнить все остальные элементы с опорным и переставить их в массиве так, чтобы разбить массив на три непрерывных отрезка, следующие друг за другом — «меньшие опорного», «равные» и «большие».
3. Для отрезков «меньших» и «больших» значений выполнить рекурсивно ту же последовательность операций, если длина отрезка больше единицы.

На практике массив обычно делят не на три, а на две части, например, «меньшие опорного» и «равные и большие». Такой подход в общем случае эффективнее, так как упрощает алгоритм разделения.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/quick_sort.gif">

Достоинства:
* Один из самых быстродействующих (на практике) из алгоритмов внутренней сортировки общего назначения.
* Прост в реализации.
* Требует лишь `O(lg n)` дополнительной памяти для своей работы. (Не улучшенный рекурсивный алгоритм в худшем случае `O(n)` памяти)
* Хорошо сочетается с механизмами кэширования и виртуальной памяти.
* Допускает естественное распараллеливание (сортировка выделенных подмассивов в параллельно выполняющихся подпроцессах).
* Допускает эффективную модификацию для сортировки по нескольким ключам (в частности — алгоритм Седжвика для сортировки строк): благодаря тому, что в процессе разделения автоматически выделяется отрезок элементов, равных опорному, этот отрезок можно сразу же сортировать по следующему ключу.
* Работает на связных списках и других структурах с последовательным доступом, допускающих эффективный проход как от начала к концу, так и от конца к началу.

Недостатки:
* Сильно деградирует по скорости (до `Theta(n^2)`) в худшем или близком к нему случае, что может случиться при неудачных входных данных.
* Прямая реализация в виде функции с двумя рекурсивными вызовами может привести к ошибке переполнения стека, так как в худшем случае ей может потребоваться сделать `O(n)` вложенных рекурсивных вызовов.
* Неустойчив
```c
int partition(int a[], int l, int r) {
  int pivot, i, j, t;
  pivot = a[l];
  i = l; j = r + 1;
  while (1) {
    do ++i; while (a[i] <= pivot && i <= r );
    do --j; while (a[j] > pivot );
    if (i >= j ) break;
    t = a[i]; a[i] = a[j]; a[j] = t;
  }
  t = a[l]; a[l] = a[j]; a[j] = t;
  return j;
}

void quickSort(int a[], int l, int r) {
  int j;
  if (l < r ) {
    // divide and conquer
    j = partition(a, l, r);
    quickSort(a, l, j - 1);
    quickSort(a, j + 1, r);
  }
}
```

<a name="merge-arrays"></a>
### How to merge two sorted arrays into a sorted array?
```c++
public static int[] merge(int[] a, int[] b) {
  int[] answer = new int[a.length + b.length];
  int i = 0, j = 0, k = 0;

  while (i < a.length && j < b.length) {
    if (a[i] < b[j])       
    answer[k++] = a[i++];

    else        
    answer[k++] = b[j++];               
  }

  while (i < a.length)  
  answer[k++] = a[i++];

  while (j < b.length)    
  answer[k++] = b[j++];

  return answer;
}
```

<a name="рекурсивная-функция"></a>
### Рекурсивная функция
Функция, вызывающая саму себя. Вопрос о желательности использования рекурсивных функций в программировании неоднозначен: с одной стороны, рекурсивная форма может быть структурно проще и нагляднее, в особенности, когда сам реализуемый алгоритм по сути рекурсивен. Кроме того, в некоторых декларативных или чисто функциональных языках (таких как Пролог или Haskell) просто нет синтаксических средств для организации циклов, и рекурсия в них — единственный доступный механизм организации повторяющихся вычислений. С другой стороны, обычно рекомендуется избегать рекурсивных программ, которые приводят (или в некоторых условиях могут приводить) к слишком большой глубине рекурсии. Так, широко распространённый в учебной литературе пример рекурсивного вычисления факториала является, скорее, примером того, как не надо применять рекурсию, так как приводит к достаточно большой глубине рекурсии и имеет очевидную реализацию в виде обычного циклического алгоритма.

Плюсы

* Наглядность
* Простота

Минусы

* Возможна большая глубина рекурсии, из-за которой может произойти быстрое переполнение стека и нехватка памяти.

__Факториал__
```c
//O(n)
int factorialRecursive(int value) {
  if (value == 1) {
    return value;
  } else {
    return value * factorialRecursive(value - 1);
  }
}

//O(n)
int factorialIterative(int value) {
  int result = 1;
  for (int number = 1; number <= value; number++) {
    result *= number;
  }
  return result;
}
```

__Последовательность Фибоначчи__
```c
//O(2^n)
int fibonacciRecursive(int position) {
  int result = 0;
  if (position < 2) {
    result = position;
  } else {
    result = fibonacciRecursive(position - 1) + fibonacciRecursive(position - 2);
  }
  return result;
}

//O(n)
int fibonacciIterative(int position) {
  int a = 1;
  int b = 1;
  int c;
  printf("%i\n%i\n", a, b);
  for (int i = 3; i <= position; i++) {
    c = a;
    a = b;
    b = c + b;
    printf("%i\n", b);
  }
  return b;
}
```

Хвостовая рекурсия — частный случай рекурсии, при котором любой рекурсивный вызов является последней операцией перед возвратом из функции.[1] Подобный вид рекурсии примечателен тем, что может быть легко заменён на итерацию путём формальной и гарантированно корректной перестройки кода функции. Оптимизация хвостовой рекурсии путём преобразования её в плоскую итерацию реализована во многих оптимизирующих компиляторах. В некоторых функциональных языках программирования спецификация гарантирует обязательную оптимизацию хвостовой рекурсии.

Типовой механизм реализации вызова функции основан на сохранении адреса возврата, параметров и локальных переменных функции в стеке и выглядит следующим образом:

В точке вызова в стек помещаются параметры, передаваемые функции, и адрес возврата.
Вызываемая функция в ходе работы размещает в стеке собственные локальные переменные.
По завершении вычислений функция очищает стек от своих локальных переменных, записывает результат (обычно - в один из регистров процессора).
Команда возврата из функции считывает из стека адрес возврата и выполняет переход по этому адресу. Одновременно стек очищается от параметров.
Таким образом, при каждом рекурсивном вызове функции создаётся новый набор её параметров и локальных переменных, который вместе с адресом возврата размещается в стеке, что ограничивает максимальную глубину рекурсии объёмом стека. В чисто функциональных или декларативных (типа Пролога) языках, где рекурсия является единственным возможным способом организации повторяющихся вычислений, это ограничение становится крайне существенным, поскольку, фактически, превращается в ограничение на число итераций в любых циклических вычислениях, при превышении которого будет происходить переполнение стека.

Нетрудно видеть, что необходимость расширения стека при рекурсивных вызовах диктуется требованием восстановления состояния вызывающего экземпляра функции (то есть её параметров, локальных данных и адреса возврата) после возврата из рекурсивного вызова. Но если рекурсивный вызов является последней операцией перед выходом из вызывающей функции и результатом вызывающей функции должен стать результат, который вернёт рекурсивный вызов, сохранение контекста уже не имеет значения — ни параметры, ни локальные переменные уже использоваться не будут, а адрес возврата уже находится в стеке. Поэтому в такой ситуации вместо полноценного рекурсивного вызова функции можно просто заменить значения параметров в стеке и передать управление на точку входа. До тех пор, пока исполнение будет идти по этой рекурсивной ветви, будет, фактически, выполняться обычный цикл. Когда рекурсия завершится (то есть исполнение пройдёт по терминальной ветви и достигнет команды возврата из функции) возврат произойдёт сразу в исходную точку, откуда произошёл вызов рекурсивной функции. Таким образом, при любой глубине рекурсии стек переполнен не будет.

```c
int fac_times(int n, int acc) {
    return (n == 0) ? acc : fac_times(n - 1, acc * n);
}
int factorial(int n) {
    return fac_times(n, 1);
}
```
