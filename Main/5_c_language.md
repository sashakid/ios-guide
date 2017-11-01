- [Язык СИ](#язык-си)
	- [Битовые операции](#битовые-операции)
	- [Примеры битовых операций](#примеры-битовых-операций)
	- [Что такое указатель и ссылка и в чем разница](#что-такое-указатель-и-ссылка-и-в-чем-разница)
	- [Почему (NSError **) использует указатель на указатель](#почему-nserror-использует-указатель-на-указатель)
	- [How to return 2+ values from a function](#how-to-return-2+-values-from-a-function)
	- [What is the difference between char* const and const char*](#what-is-the-difference-between-char-const-and-const-char)
	- [Что значит n&(n – 1)](#что-значит-n-n–1)

<a name="язык-си"></a>
# Язык СИ.

* Лаконичность и быстрота (почти как Ассемблер)
* Переносимость на различные архитектуры
* Набор низкоуровневых средств
* Прямой доступ к памяти
* Операции над битами
* Адресная арифметика

Си – универсальный язык программирования, считается удобным для системного программирования, хотя он удобен и для написания прикладных программ. Среди преимуществ языка Си следует отметить переносимость программ на компьютеры различной архитектуры и из одной операционной системы в другую, лаконичность записи алгоритмов, логическую стройность программ, а также возможность получить программный код, сравнимый по скорости выполнения с программами, написанными на языке ассемблера. Последнее связано с тем, что хотя Си является языком высокого уровня, имеющим полный набор конструкций структурного программирования, он также обладает набором низкоуровневых средств, обеспечивающих доступ к аппаратным средствам компьютера.
Программа на Cи состоит из программных единиц одного типа – функций. Аргументы могут передаваться функциям посредством копирования значений этих аргументов; при этом вызванная функция не может изменить фактический аргумент в вызывающей подпрограмме.
Возможен иной вариант – передача параметра по ссылке, когда явно передается указатель, т.е. адрес, при этом функция сможет изменить объект, на который ссылается указатель.
В Си предусмотрен ряд операций низкого уровня: прямой доступ к памяти, операции над битами данных и адресной арифметики.
Программы на языке Си компактны и гибки. Язык Си доверяет программисту и разрешает ему практически все; из-за этого Си нельзя считать языком надежного программирования, и вся ответственность за качество программы лежит на программисте, который должен знать особенности языка и его реализации. Программа, написанная на языке Си, состоит из операторов. Каждый оператор вызывает выполнение некоторых действий на соответствующем шаге выполнения программы.
При написании операторов применяются латинские прописные и строчные буквы, цифры и специальные знаки. К таким знакам, например, относятся: точка `.`, запятая `,`, двоеточие `:`, точка с запятой `;` и др. Совокупность символов, используемых в языке, называется алфавитом языка. Программы оперируют с различными данными, которые могут быть простыми и структурированными. Простые данные - это целые и вещественные числа, символы и указатели (адреса объектов в памяти). Целые числа не имеют, а вещественные имеют дробную часть. Структурированные данные - это массивы и структуры.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/c_types.png">

<a name="битовые-операции"></a>
## Битовые операции
В своих программах вы не адресуете отдельные биты, а имеете дело с группами битов - байтами. Если представить байт как 8-разрядное целое число без знака, его биты соответствуют последовательным степеням `2`.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/binary.png">

Однако компьютерам удобнее иметь дело со степенями `2`. Программисты часто используют шестнадцатеричную систему (`16 = 2^4`) - особенно при работе с отдельными разрядами целых чисел. В качестве дополнительных цифр в шестнадцатеричной системе используются буквы `а`, `b`, `с`, `d`, `е` и `f`. Таким образом, счет в шестнадцатеричной системе выглядит так: `0 1 2 3 4 5 6 7 8 9 а b с d е f 10 11 ...` Числа, записанные в шестнадцатеричной системе, обозначаются префиксом `0х`.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/hexadecimal.png">

Один байт всегда может быть представлен шестнадцатеричным числом из двух цифр (например, `3с`). По этой причине шестнадцатеричные числа удобны для работы с двоичными данными.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/numeral_system.png">

__Побитовое `И` (`AND`, `&`)__

`2` байта можно объединить поразрядной операцией `И` для создания третьего байта. В этом случае бит третьего байта равен `1` только в том случае, если оба соответствующих бита первых двух байтов равны `1`.
```
0011
0101
----
0001
```
Часто используется для обнуления некоторой группы разрядов. Например:
```c
n = n & 0177;
```
обнуляет в `n` все разряды, кроме младших семи.

__Побитовое `ИЛИ` (`OR`, `|`)__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/or_example.png">

Программа выдает результат объединения двух байтов поразрядной операцией `ИЛИ`:
```
Hex: 		03c0 | 0a90 = 0bd
Decimal: 	0600 | 01690 = 0189
```
```
0011
0101
----
0111
```
Применяют для установки разрядов; так,
```c
х = х | SET_ON;
```
устанавливает единицы в тех разрядах `х`, которым соответствуют единицы в `SET_ON`.

__Побитовое исключающее `ИЛИ` (сложение по модулю два, `XOR`, `^`)__

Исключающая операция `ИЛИ` объединяет два байта и создает третий байт. Бит результата равен `1` в том случае, если ровно один из двух соответствующих битов входных байтов равен `1`.
```
0011
0101
----
0110
```

__Побитовое отрицание (дополнение, унарный оператор `НЕ`, `NOT`, `~`)__

Дополнением к существующему байту называется байт, биты которого находятся в противоположном состоянии: все нули заменяются единицами, а все единицы заменяются нулями.
```
0011
----
1100
```
Унарный оператор `~` поразрядно "обращает" целое т.е. превращает каждый единичный бит в нулевой и наоборот. Например:
```c
х = х & ~077
```
обнуляет в `х` последние `6` разрядов. Заметим, что запись `х & ~077` не зависит от длины слова, и, следовательно, она лучше, чем `х & 0177700`, поскольку последняя подразумевает, что `х` занимает `16` битов. Не зависимая от машины форма записи `~077` не потребует дополнительных затрат при счете, так как `~077` — константное выражение, которое будет вычислено во время компиляции.

__Сдвиг влево `<<`__

При выполнении операции сдвига влево каждый бит смещается в направлении старшего бита. Биты, выходящие за пределы числа, теряются, а возникающие справа «пустоты» заполняются нулями.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/left_bitwise.png">

__Сдвиг вправо `>>`__

__Примеры битовых операций:__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/bit_example.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/bit_math_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/bit_math_2.png">

```
67 & 114 = 66
67 | 114 = 115
67 ^ 114 = 49
~67 = 188
```

<a name="что-такое-указатель-и-ссылка-и-в-чем-разница"></a>
## Что такое указатель и ссылка и в чем разница?
Есть два способа обращения к функции – вызов по значению и вызов по ссылке. При вызове по значению создается копия аргумента и передается вызываемой функции. Изменение копии не влияют на значение оригинала в операторе вызова. Один из минусов этого способа – если передается большой элемент данных, то на его копирование может уйти дополнительное время.

Ссылочный параметр – это псевдоним аргумента.
```c
int &count; //count является ссылкой на int.
```
В вызове функции достаточно указать имя переменной и она будет передана по ссылке, тогда упоминание в теле вызываемой функции переменной по имени ее параметра в действительности является обращением к исходной переменной в вызывающей функции и эта исходная переменная может быть изменена непосредственно вызываемой функцией. Для передачи больших объектов используется константный ссылочный параметр, чтобы обеспечить защиту параметра, как при вызове по значению, и в то же время избежать накладных расходов при передаче копии большого объекта:
```c
const int &count;
```
__Ссылка__ – это псевдоним для другой переменной и все операции, выполняемые с псевдонимом (ссылкой) выполняются на самом деле с истинной переменной. Псевдоним – другое имя переменной и для него не резервируется место в памяти.
Если возвращение ссылки переменной объявлено в функции, то эта переменная должна быть объявлена внутри функции как статическая, иначе ссылка адресуется автоматической переменной, которая после выполнения функции уничтожается.

__Указатель__ – переменная, которая содержит в качестве значения адрес памяти переменной, которая уже в свою очередь содержит значение. Т.о. имя переменной отсылает к значению прямо, а указатель – косвенно.
```c
int y = 5;
int *yPtr;
yPtr = &y;
```
Теперь `yPtr` указывает на `y`.
Операция `*` – операция косвенной адресации или операция разыменования.

Аргументы можно передавать в функцию тремя способами:

1. Вызов по значению
2. Вызов по ссылке с аргументами ссылками
3. Вызов по ссылке с аргументами указателями

Указатели как и ссылки тоже можно использовать для модификации одного или более значений переменных в вызывающем операторе, или передавать указатели на большие объекты данных, чтобы избежать расходов, сопутствующих передаче объектов по значению.

`const` с указателем значит, что значение переменной не изменяется.

<a name="почему-nserror-использует-указатель-на-указатель"></a>
## Почему (NSError **) использует указатель на указатель?
_Explanation 1:_
if you pass a pointer to an object to your function, the function can only modify what the pointer is pointing to.
if you pass a pointer to a pointer to an object then the function can modify the pointer to point to another object.
In the case of `NSError`, the function might want to create a new `NSError` object and pass you back a pointer to that `NSError` object. Thus, you need double indirection so that the pointer can be modified.

_Explanation 2:_
A pointer to a pointer is a form of multiple indirection, or a chain of pointers. Normally, a pointer contains the address of a variable. When we define a pointer to a pointer, the first pointer contains the address of the second pointer, which points to the location that contains the actual value as shown below.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/pointers.png">

A variable that is a pointer to a pointer must be declared as such. This is done by placing an additional asterisk in front of its name. For example, the following declaration declares a pointer to a pointer of type `int`: `int **var;`
When a target value is indirectly pointed to by a pointer to a pointer, accessing that value requires that the asterisk operator be applied twice, as is shown below in the example:
```c
int main () {

  int  var;
  int  *ptr;
  int  **pptr;

  var = 3000;

  /* take the address of var */
  ptr = &var;

  /* take the address of ptr using address of operator & */
  pptr = &ptr;

  /* take the value using pptr */
  printf("Value of var = %d\n", var);
  printf("Value available at *ptr = %d\n", *ptr);
  printf("Value available at **pptr = %d\n", **pptr);

  return 0;
}
```
```
Value of var = 3000
Value available at *ptr = 3000
Value available at **pptr = 3000
```
with a regular parameter, say `int`, you get a local copy

with a pointer parameter, say `int*`, you can modify what it points to

with a double pointer parameter, say `int**`, you can modify the pointer itself, i.e. 'repoint' it

## How to return 2+ values from a function?

__In C:__

* Returning the address of the first element of a local array has undefined behavior (at least dereferencing it later is). You may use output parameters, that is, pass two pointers, and set the values inside:
```c
void Calculate(int x, int y, int* prod, int* quot) {
  *prod = x*y;
  *quot = x/y;
}
```
Usage:
```c
int x = 10, y = 2, prod, quot;
Calculate(x, y, &prod, &quot)
```
* Another thing you could do is pack your data into a struct

```c
typedef struct {
  int prod;
  int quot;
} product_and_quot;

product_and_quot Calculate(int x, int y) {
  product_and_quot p = {x*y, x/y};
  return p;
}
```
__in Objective-C:__

* Pointers

```objectivec
- (void)convertA:(float)a B:(float)b C:(float) intoX:(float *)xOut Y:(float *)yOut Z:(float)zOut {
  *xOut = 3*a + b;
  *yOut = 2*b;
  *zOut = a*b + 4*c;
}
```
and call it like this:
```objectivec
float x, y, z;
[self convertA:a B:b C:c intoX:&x Y:&y Z:&z];
```
* Another way is to create a struct and return it:

```objectivec
struct XYZ {
  float x, y, z;
};

- (struct XYZ)xyzWithA:(float)a B:(float)b C:(float)c {
  struct XYZ xyz;
  xyz.x = 3*a + b;
  xyz.y = 2*b;
  xyz.z = a*b + 4*c;
  return xyz;
}
```
Call it like this:
```objectivec
struct XYZ output = [self xyzWithA:a B:b C:c];
```
* Double pointers with objects

If you want to return more than one new object, your function should take pointers to the object pointer, thus:
```objectivec
- (void)mungeFirst:(NSString **)stringOne andSecond:(NSString **)stringTwo {
  *stringOne = [NSString stringWithString:@"foo"];
  *stringTwo = [NSString stringWithString:@"baz"];
}
```
* Blocks

You can return two values with help of block:
```objectivec
- (void)getUIControlles:(void (^)(UITextField *objTextFiled, UIView *objView))completionBlock {
  UITextField * textFiled = nil;
  /*
  do code here for textfiled
  */
  UIView * viewDemo = nil;

  /*
  do code here for Uiview.
  */

  completionBlock (textFiled, viewDemo);
}

- (void)testMethod {
  // Call function with following way.
  [self getUIControlles:^(UITextField *objTextFiled, UIView *objView) {
    // objTextFiled = This is your textfiled object
    // objView = This is your view object
    }];
  }
  ```

<a name="what-is-the-difference-between-char-const-and-const-char"></a>
## What is the difference between char * const and const char *?

Существует четыре способа передачи в функцию указателя

1. Неконстантный указатель на неконстантные данные
2. Неконстнатный указатель на константные данные
3. Константный указатель на неконстантные данные
4. Константный указатель на константные данные

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/const_pointer.png">

<a name="что-значит-n-n–1"></a>
## Что значит n&(n – 1)?
It's figuring out if `n` is either `0` or an exact power of two.
It works because a binary power of two is of the form `1000...000` and subtracting one will give you `111...111`. Then, when you `AND` those together, you get zero, such as with:
```
  1000 0000 0000 0000
&  111 1111 1111 1111
  ==== ==== ==== ====
= 0000 0000 0000 0000
```
Any non-power-of-two input value will not give you zero when you perform that operation.
For example, let's try all the 3-bit combinations:
```
<----- binary ---->
  n     n    n-1   n&(n-1)
---   ---   ---   -------
 0    000   111     000 *
 1    001   000     000 *
 2    010   001     000 *
 3    011   010     010
 4    100   011     000 *
 5    101   100     100
 6    110   101     100
 7    111   110     110
```
You can see that only `0` and the powers of two (`1`, `2` and `4`) result in a `000-false` bit pattern, all others are non-zero or `true`.
See the full Bit Twiddling Hacks document for all sorts of other wonderful (or dastardly, depending on your viewpoint) hackery.
