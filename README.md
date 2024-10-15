# Тема 6. Базовые коллекции: словари, кортежи
Отчет по Теме #6 выполнил(а):
- Мордиков Артем Владимирович
- ПИЭ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
### В школе, где вы учились, узнали, что вы крутой программист и попросили написать программу для учителей, которая будет при вводе кабинета писать для него ключ доступа и статус, занят кабинет или нет. При написании программы необходимо использовать словарь (dict), который на вход получает номер кабинета, а выводит необходимую информацию. Если кабинета, который вы ввели нет в словаре, то в консоль в виде значения ключа нужно вывести “None” и виде статуса вывести “False”. По большому счету написав данную программу мы с вами научились заменять иногда громоздкую конструкцию if/elif/else. Поскольку здесь функционал словаря полностью повторяет функционал условия, но при этом у использования словарей в более сложных программах есть намного больше возможностей реализации.

## Код
```python
request = int(input('Введите номер кабинета: '))

dictionary = {
    101: {'key': 1234, 'access': True},
    102: {'key': 1337, 'access': True},
    103: {'key': 8943, 'access': True},
    104: {'key': 5555, 'access': False},
    None: {'key': None, 'access': False},
}

response = dictionary.get(request)
if not response:
    response = dictionary[None]
key = response.get('key')
access = response.get('access')
print(key, access)
```

### Результат.
![image](https://github.com/user-attachments/assets/5f2291f8-1b7d-4933-9da4-2309bea116d0)


## Лабораторная работа №2
### Алексей решил создать самый большой словарь в мире. Для этого он придумал функцию dict_maker (**kwargs), которая принимает неограниченное количество параметров «ключ: значение» и обновляет  созданный им словарь my_dict, состоящий всего из одного элемента «first» со значением «so easy». Помогите Алексею создать данную функцию. Ниже на скриншоте мы использовали встроенный модуль pprint, который выводит большие объемы информации более понятно для восприятия человеческим глазом. Иногда очень удобно использовать данную возможность Python.

## Код
```python
from pprint import pprint

my_dict = {'first': 'so easy'}


def dict_maker(**kwargs):
    my_dict.update(**kwargs)
    
    
dict_maker(a1=1, a2=20, a3=54, a4=13)
dict_maker(name='Михаил', age=31, weight=70, eyes_color='blue')
pprint(my_dict)
```

### Результат.
![image](https://github.com/user-attachments/assets/c1f15a6e-ac2a-40ed-8444-e5b906771b40)


## Лабораторная работа №3
### Для решения некоторых задач бывает необходимо разложить строку на отдельные символы. Мы знаем что это можно сделать при помощи split(), у которого более гибкая настройка для разделения для этого, но если нам нужно посимвольно разделить строку без всяких условий, то для этого мы можем использовать кортежи (tuple). Для этого напишем любую строку, которую будем делить и “обвернем” ее в tuple и дальше мы можем как нам угодно с ней работать, например, сделать ее списком (тогда получится полный аналог split()) или же работать с ним дальше, как с кортежем.

## Код
```python
input_string = "HelloWorld"
result = tuple(input_string)
print(result)
print(list(result))
```

### Результат.
![image](https://github.com/user-attachments/assets/126f002f-6b03-4de4-8c4b-2c36f851abbb)


## Лабораторная работа №4
### Вовочка решил написать крутую функцию, которая будет писать имя, возраст и место работы, но при этом на вход этой функции будет поступать кортеж. Помогите Вовочке написать эту программу.

## Код
```python
def personal_info(name, age, company='unnamed'):
    print(f"Имя: {name} Возраст: {age} Компания: {company}")
    
    
tom = ("Григорий", 22)
personal_info(*tom)

bob = ("Георгий", 41, "Yandex")
personal_info(*bob)
```

### Результат.
![image](https://github.com/user-attachments/assets/baf2935f-621c-426f-b663-9f922e944082)


## Лабораторная работа №5
### Для сопровождения первых лиц государства X нужен кортеж, но никто не может определиться с порядком машин, поэтому вам нужно написать функцию, которая будет сортировать кортеж, состоящий из целых чисел по возрастанию, и возвращает его. Если хотя бы один элемент не является целым числом, то функция возвращает исходный кортеж.

## Код
```python
def tuple_sort(tpl):
    for elm in tpl:
        if not isinstance(elm, int):
            return tpl
    return tuple(sorted(tpl))


if __name__ == '__main__':
    print(tuple_sort((5, 5, 3, 1, 9)))
    print(tuple_sort((5, 5, 2.1, '1', 9)))
```

### Результат.
![image](https://github.com/user-attachments/assets/94dbfe1e-bfc9-49fc-9d9a-8ec77a2879ce)

## Самостоятельная работа №1
### При создании сайта у вас возникла потребность обрабатывать данные пользователя в странной форме, а потом переводить их в нужные вам форматы. Вы хотите принимать от пользователя последовательность чисел, разделенных пробелом, а после переформатировать эти данные в список и кортеж. Реализуйте вашу задумку. Для получения начальных данных используйте input(). Результатом программы будет выведенный список и кортеж из начальных данных

## Код
```python
data = input("Введите последовательность чисел, разделенных пробелами: ")
data_list = data.split()
data_tuple = tuple(data_list)
print("Список:", data_list)
print("Кортеж:", data_tuple)
```

### Результат.
![image](https://github.com/user-attachments/assets/3b25ff9b-bdb5-4f47-bfdd-06fcd39a9a37)

### Вывод:
Код получает строку чисел, разделенных пробелами, преобразует её в список и кортеж, затем выводит оба результата.

## Самостоятельная работа №2
### Николай знает, что кортежи являются неизменяемыми, но он очень упрямый и всегда хочет доказать, что он прав. Студент решил создать функцию, которая будет удалять первое появление определенного элемента из кортежа по значению и возвращать кортеж без него. Попробуйте повторить шедевр не признающего авторитеты начинающего программиста. Но учтите, что Николай не всегда уверен в наличии элемента в кортеже (в этом случае кортеж вернется функцией в исходном виде).
Входные данные:
(1, 2, 3), 1)
(1, 2, 3, 1, 2, 3, 4, 5, 2, 3, 4, 2, 4, 2), 3)
(2, 4, 6, 6, 4, 2), 9)
Ожидаемый результат:
(2, 3)
(1, 2, 1, 2, 3, 4, 5, 2, 3, 4, 2, 4, 2)
(2, 4, 6, 6, 4, 2)

## Код
```python
def remove_first_occurrence(tpl, element):
    if element in tpl:
        lst = list(tpl)
        lst.remove(element)
        return tuple(lst)
    return tpl


print(remove_first_occurrence((1, 2, 3), 1))
print(remove_first_occurrence((1, 2, 3, 1, 2, 3, 4, 5, 2, 3, 4, 2, 4, 2), 3))
print(remove_first_occurrence((2, 4, 6, 6, 4, 2), 9))

```

### Результат.
![image](https://github.com/user-attachments/assets/bf7d0713-6c7d-4dd1-9072-d69ba95cc8ce)

### Вывод:
1. Если элемент присутствует в кортеже, функция удаляет первое его вхождение и возвращает новый кортеж.
2. Если элемент отсутствует, возвращается исходный кортеж.

## Самостоятельная работа №3
### Ребята поспорили кто из них одним нажатием на numpad наберет больше повторяющихся цифр, но не понимают, как узнать победителя. Вам им нужно в этом помочь. Дана строка в виде случайной последовательности чисел от 0 до 9 (длина строки минимум 15 символов). Требуется создать словарь, который в качестве ключей будет принимать данные числа (т. е. ключи будут типом int), а в качестве значений – количество этих чисел в имеющейся последовательности. Для построения словаря создайте функцию, принимающую строку из цифр. Функция должна возвратить словарь из 3-х самых часто встречаемых чисел, также эти значения нужно вывести в порядке возрастания ключа.

## Код
```python
from collections import Counter


def top_three_digits(s):
    counter = Counter(map(int, s))
    most_common = counter.most_common(3)
    result = {k: v for k, v in sorted(most_common)}
    return result


s = "123456789123456"
print(top_three_digits(s))

```

### Результат.
![image](https://github.com/user-attachments/assets/0afd7dfe-d985-4360-bd91-88d74080bff3)

### Вывод:
Программа подсчитывает количество вхождений каждой цифры в строке, находит три наиболее часто встречающиеся цифры и выводит их в виде словаря, где ключи — цифры, а значения — количество их вхождений.

## Самостоятельная работа №4
### Ваш хороший друг владеет офисом со входом по электронным картам, ему нужно чтобы вы написали программу, которая показывала в каком порядке сотрудники входили и выходили из офиса. Определение сотрудника происходит по id. Напишите функцию, которая на вход принимает кортеж и случайный элемент (id), его можно придумать самостоятельно. Требуется вернуть новый кортеж, начинающийся с первого появления элемента в нем и заканчивающийся вторым его появлением включительно. Если элемента нет вовсе – вернуть пустой кортеж. Если элемент встречается только один раз, то вернуть кортеж, который начинается с него и идет до конца исходного.
Входные данные:
(1, 2, 3), 8)
(1, 8, 3, 4, 8, 8, 9, 2), 8)
(1, 2, 8, 5, 1, 2, 9), 8)
Ожидаемый результат:
()
(8, 3, 4, 8)
(8, 5, 1, 2, 9)

## Код
```python
def find_subtuple(tpl, element):

    if tpl.count(element) == 0:
        return ()
    
    first_index = tpl.index(element)

    if tpl.count(element) == 1:
        return tpl[first_index:]
    
    second_index = tpl.index(element, first_index + 1)

    return tpl[first_index:second_index + 1]


print(find_subtuple((1, 2, 3), 8))
print(find_subtuple((1, 8, 3, 4, 8, 8, 9, 2), 8))
print(find_subtuple((1, 2, 8, 5, 1, 2, 9), 8)) 

```

### Результат.
![image](https://github.com/user-attachments/assets/2a6169a6-cfcd-487b-926e-e8a0d1aefc5f)

### Вывод:
Программа ищет первое и второе вхождение элемента в кортеже. Если элемент найден только один раз, она возвращает кортеж от его первого вхождения до конца. Если элемент встречается дважды, возвращает часть кортежа от первого до второго вхождения включительно. Если элемент не найден, возвращает пустой кортеж.

## Самостоятельная работа №5
### Самостоятельно придумайте и решите задачу, в которой будут обязательно использоваться кортеж или список. Проведите минимум три теста для проверки работоспособности вашей задачи. 
### Написать функцию, которая принимает список чисел и возвращает кортеж, содержащий только уникальные числа из списка, отсортированные в порядке возрастания.

def unique_sorted_tuple(lst):
    return tuple(sorted(set(lst)))

## Код
```python
print(unique_sorted_tuple([3, 1, 2, 3, 4, 1]))
print(unique_sorted_tuple([5, 5, 5, 5]))
print(unique_sorted_tuple([9, 8, 7, 6]))
```

### Результат.
![image](https://github.com/user-attachments/assets/c0b6ee36-9553-4dbe-8b64-becc23587c1e)

### Вывод:
Функция принимает список чисел, удаляет дубликаты с помощью преобразования в множество, затем сортирует элементы и возвращает результат в виде кортежа. Тесты показывают, что функция корректно обрабатывает списки с повторяющимися числами, удаляя дубликаты и сортируя значения.

## Общий вывод:
В ходе выполнения заданий я научился работать со списками, кортежами и словарями в Python. Закрепил навыки обработки данных: преобразование, сортировка, удаление дубликатов, поиск элементов. Также научился писать функции, которые учитывают различные случаи, и использовать неизменяемые коллекции для хранения данных. Работа помогла лучше понять применение коллекций для решения практических задач.

