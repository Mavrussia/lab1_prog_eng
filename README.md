# Тема 7. Работа с файлами (ввод, вывод)
Отчет по Теме #7 выполнил(а):
- Мордиков Артем Владимирович
- ПИЭ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |
| Задание 6 | + | 
| Задание 7 | + | 
| Задание 8 | + | 
| Задание 9 | + | 
| Задание 10 |+ |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1

### Составьте текстовый файл и положите его в одну директорию с
программой на Python. Текстовый файл должен состоять минимум из
двух строк

### Результат.
![image](https://github.com/user-attachments/assets/0dd93b18-05ff-42bf-808e-12be64cc694e)


## Лабораторная работа №2
### Напишите программу, которая выведет только первую строку из
вашего файла, при этом используйте конструкцию open()/close().

```python
f = open('statia.txt', 'r')
print(f.readline())
f.close()
```

### Результат.
![image](https://github.com/user-attachments/assets/546a0407-9e22-4a9c-88ed-9cb8d68c1f46)


## Лабораторная работа №3
### Напишите программу, которая выведет все строки из вашего файла в
массиве, при этом используйте конструкцию open()/close().

### Код
```python
f = open('statia.txt', 'r', encoding='utf-8')
print(f.readlines())
f.close()
```

### Результат.
![image](https://github.com/user-attachments/assets/cadc9d47-7e2c-4803-8380-2d189c50d635)

## Лабораторная работа №4
### Напишите программу, которая выведет все строки из вашего файла в
массиве, при этом используйте конструкцию with open()
### Код
```python
with open('statia.txt', encoding='utf-8') as f:
    print(f.readlines())
```

### Результат.
![image](https://github.com/user-attachments/assets/81cc1545-573a-4c99-81a6-6fd34c112e80)

## Лабораторная работа №5
### Напишите программу, которая выведет каждую строку из вашего
файла отдельно, при этом используйте конструкцию with open()
### Код
```python
with open('statia.txt', encoding='utf-8') as f:
    for line in f:
        print(line)
```

### Результат.
![image](https://github.com/user-attachments/assets/26d6f57e-da40-4147-8f93-d02de7f4fb58)

## Лабораторная работа №6
### Напишите программу, которая будет добавлять новую строку в ваш
файл, а потом выведет полученный файл в консоль. Вывод можно
осуществлять любым способом. Обязательно проверьте сам файл,
чтобы изменения в нем тоже отображались
### Код
```python
with open('statia.txt', 'a+', encoding='utf-8') as f:
    f.write('\nIn additional line')

with open('statia.txt', 'r', encoding='utf-8') as f:
    result = f.readlines()
    print(result)

```

### Результат.
![image](https://github.com/user-attachments/assets/4224f145-3a61-4a39-b2d0-f7a6ad354f93)

## Лабораторная работа №7
### Напишите программу, которая перепишет всю информацию, которая
была у вас в файле до этого, например напишет любые данные из
произвольно вами составленного списка. Также не забудьте проверить
что измененная вами информация сохранилась в файле.
### Код
```python
lines = ['one', 'two', 'three']
with open('statia.txt', 'w', encoding='utf-8') as f:
    for line in lines:
        f.write('\nCycle run ' + line)
    print('Done!')
```

### Результат.
![image](https://github.com/user-attachments/assets/f3058c60-9b99-4759-92ad-7d8eebb0264e)
![image](https://github.com/user-attachments/assets/da879111-8a53-44b5-bfda-fb22bff5f5bf)

## Лабораторная работа №8
### Выберите любую папку на своем компьютере, имеющую вложенные
директории. Выведите на печать в терминал ее содержимое, как и всех
подкаталогов при помощи функции print_docs(directory).
### Код
```python
import os


def print_docs(directory):
    all_files = os.walk(directory)
    for catalog in all_files:
        print(f'Папка {catalog[0]} содержит:')
        print(f'Директории: {", ".join([folder for folder in catalog[1]])}')
        print(f'Файлы: {", ".join([file for file in catalog[2]])}')
        print('-' * 40)
    
    
print_docs('C:\Python Ургэу\TEMA_7')
```

### Результат.
![image](https://github.com/user-attachments/assets/d0d0dc71-410a-45d6-90a3-3ad612383478)

## Лабораторная работа №9
### Документ «input.txt» содержит следующий текст:
Приветствие
Спасибо
Извините
Пожалуйста
До свидания
Ты готов?
Как дела?
С днем рождения!
Удача!
Я тебя люблю.
Требуется реализовать функцию, которая выводит слово, имеющее
максимальную длину (или список слов, если таковых несколько).
Проверьте работоспособность программы на своем наборе данных

### Код
```python
def longest_words(file):
    with open(file, encoding='utf-8') as f:
        words = f.read().split()
        max_length = len(max(words, key=len))
        sought_words = [word for word in words if len(word) == max_length]
                
        if len(sought_words) == 1:
            return sought_words[0]
        return sought_words
    
    
print(longest_words('input.txt'))
```

### Результат.
![image](https://github.com/user-attachments/assets/fa6c472b-aa20-4a2a-a87c-9a061944d121)


## Лабораторная работа №10
### Требуется создать csv-файл «rows_300.csv» со следующими
столбцами:
• № - номер по порядку (от 1 до 300);
• Секунда – текущая секунда на вашем ПК;
• Микросекунда – текущая миллисекунда на часах.
Для наглядности на каждой итерации цикла искусственно
приостанавливайте скрипт на 0,01 секунды.
### Код
```python
import csv
import datetime
import time


with open('rows_300.csv', 'w', encoding='utf-8', newline='') as f:
    writer = csv.writer(f)
    writer.writerow(['№', 'Секунда', 'Микросекунда'])
    for line in range(1, 301):
        writer.writerow([line, datetime.datetime.now().second, datetime.datetime.now().microsecond])
        time.sleep(0.01)
```

### Результат.

![image](https://github.com/user-attachments/assets/09a427b6-ab87-4ec4-8731-82f0441dae32)

## Самостоятельная работа №1
### Найдите в интернете любую статью (объем статьи не менее 200 слов), скопируйте ее содержимое в файл и напишите программу, которая считает количество слов в текстовом файле и определит самое часто встречающееся слово. Результатом выполнения задачи будет: скриншот файла со статьей, листинг кода, и вывод в консоль, в котором будет указана вся необходимая информация.

### Код
```python
from collections import Counter
import string

with open('statia.txt', 'r', encoding='utf-8') as file:
    text = file.read()

translator = str.maketrans('', '', string.punctuation)
clean_text = text.translate(translator).lower()

words = clean_text.split()

if words:
    word_count = len(words)
    word_frequencies = Counter(words)
    most_common_word, most_common_count = word_frequencies.most_common(1)[0]

    print(f"Общее количество слов в статье: {word_count}")
    print(f"Самое часто встречающееся слово: '{most_common_word}', встречается {most_common_count} раз(а)")
else:
    print("Файл пустой или не содержит слов.")

```

### Результат.
![image](https://github.com/user-attachments/assets/de80fbeb-2d0f-49c6-a9e9-2f471d20767b)

### Вывод
Программа успешно подсчитывает количество слов в файле и определяет самое часто встречающееся слово с помощью модуля Counter.

## Самостоятельная работа №2
### У вас появилась потребность в ведении книги расходов, посмотрев
все существующие варианты вы пришли к выводу что вас ничего не
устраивает и нужно все делать самому. Напишите программу для
учета расходов. Программа должна позволять вводить информацию
о расходах, сохранять ее в файл и выводить существующие данные в
консоль. Ввод информации происходит через консоль. Результатом
выполнения задачи будет: скриншот файла с учетом расходов,
листинг кода, и вывод в консоль, с демонстрацией
работоспособности программы
### Код
```python
def add_expense():
    expense = input("Введите описание расхода: ")
    amount = input("Введите сумму расхода: ")
    
    with open('expenses.txt', 'a', encoding='utf-8') as file:
        file.write(f"{expense}: {amount} руб.\n")
    
    print("Расход добавлен.\n")

def show_expenses():
    try:
        with open('expenses.txt', 'r', encoding='utf-8') as file:
            print("Текущие расходы:")
            print(file.read())
    except FileNotFoundError:
        print("Расходов пока нет.\n")

def main():
    while True:
        print("1. Добавить расход")
        print("2. Показать все расходы")
        print("3. Выйти")
        
        choice = input("Выберите действие: ")
        
        if choice == '1':
            add_expense()
        elif choice == '2':
            show_expenses()
        elif choice == '3':
            print("Выход из программы.")
            break
        else:
            print("Неверный выбор. Попробуйте снова.\n")

if __name__ == '__main__':
    main()

```

### Результат.
![image](https://github.com/user-attachments/assets/f5e93d3c-6247-4cdb-9eb9-c5acfa08b0fa)

### Вывод
Программа для учета расходов корректно записывает новые расходы в файл и выводит существующие данные из файла, обеспечивая удобный просмотр расходов.

## Самостоятельная работа №3
### Имеется файл input.txt с текстом на латинице. Напишите программу,
которая выводит следующую статистику по тексту: количество букв
латинского алфавита; число слов; число строк.
• Текст в файле:
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
• Ожидаемый результат:
Input file contains:
108 letters
20 words
4 lines
### Код
```python
def text_statistics(file):
    with open(file, 'r', encoding='utf-8') as f:
        text = f.read()

    lines = text.splitlines()
    num_lines = len(lines)

    words = text.split()
    num_words = len(words)

    letters = [char for char in text if char.isalpha() and char.isascii()]
    num_letters = len(letters)

    print(f"Input file contains:")
    print(f"{num_letters} letters")
    print(f"{num_words} words")
    print(f"{num_lines} lines")


text_statistics('input.txt')

```

### Результат.
![image](https://github.com/user-attachments/assets/db68c425-8a02-442a-ace0-647f558d8079)

### Вывод
Программа правильно подсчитывает количество букв, слов и строк в файле, работая с латинскими символами.

## Самостоятельная работа №4
### Напишите программу, которая получает на вход предложение,
выводит его в терминал, заменяя все запрещенные слова
звездочками * (количество звездочек равно количеству букв в
слове). Запрещенные слова, разделенные символом пробела,
хранятся в текстовом файле input.txt. Все слова в этом файле
записаны в нижнем регистре. Программа должна заменить
запрещенные слова, где бы они ни встречались, даже в середине
другого слова. Замена производится независимо от регистра: если файл input.txt содержит запрещенное слово exam, то слова exam,
Exam, ExaM, EXAM и exAm должны быть заменены на ****.
• Запрещенные слова:
hello email python the exam wor is
• Предложение для проверки:
Hello, world! Python IS the programming language of thE future. My EMAIL is.... PYTHON is awesome!!!!
• Ожидаемый результат:
*****, ***ld! ****** ** *** programming language of *** future. My
***** **....
****** ** awesome!!!!
### Код
```python
import re
def censor_text(text, banned_words):
    for word in banned_words:
        text = re.sub(rf'(?i){word}', '*' * len(word), text)
    return text
with open('input1.txt', 'r', encoding='utf-8') as f:
    banned_words = f.read().split()
text = input("Введите предложение: ")
censored_text = censor_text(text, banned_words)
print(censored_text)

```

### Результат.
![image](https://github.com/user-attachments/assets/28fdc29b-b7b2-4454-aa7f-3e3f3f2f1e37)


### Вывод
Программа заменяет запрещенные слова звездочками независимо от регистра с использованием регулярных выражений, что соответствует требованиям задачи.

## Самостоятельная работа №5
### Самостоятельно придумайте и решите задачу, которая будет
взаимодействовать с текстовым файлом
Подсчет количества предложений в текстовом файле
### Код
```python
def count_sentences(file):

    with open(file, 'r', encoding='utf-8') as f:
        text = f.read()
        
    sentences = text.count('.') + text.count('!') + text.count('?')

    print(f"Количество предложений в файле: {sentences}")


count_sentences('input.txt')

```

### Результат.
![image](https://github.com/user-attachments/assets/9f589d2d-a32b-4b46-879a-f0ec4108b1d1)

![image](https://github.com/user-attachments/assets/4c03e7a5-42fc-48bd-8897-d12e3cbf2bc1)

### Вывод
Программа подсчитывает количество предложений в текстовом файле на основе знаков препинания (точка, восклицательный и вопросительный знак).

### Общий вывод
В процессе выполнения этих заданий я научился эффективно взаимодействовать с текстовыми файлами, обрабатывать данные, производить вычисления и выводить результаты. Также удалось освоить работу с текстом для решения различных задач: подсчет слов, строк, символов, замена запрещённых слов, а также создание простых систем для ведения учёта данных, таких как книга расходов.
