# Тема 9. Концепции и принципы ООП
Отчет по Теме #9 выполнил(а):
- Мордиков Артем Владимирович
- ПИЭ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | 
| Задание 3 | + | 
| Задание 4 | + | 
| Задание 5 | + | 


знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
### Допустим, что вы решили оригинально и немного странно познакомится
с человеком. Для этого у вас должен быть написан свой класс на Python,
который будет проверять угадал ваше имя человек или нет. Для этого
создайте класс, указав в свойствах только имя. Дальше создайте
функцию __init__(), а в ней сделайте проверку на то угадал человек ваше
имя или нет. Также можете проверить что будет, если в этой функции
указав атрибут, который не указан в вашем классе, например,
попробуйте вызвать фамилию.

```python
class Ivan:
    __slots__ = ['name']
    
    def __init__(self, name):
        if name == 'Иван':
            self.name = (f"Да, я {name}")
        else:
            self.name = (f"Я не {name}, а Иван")
            
            
person1 = Ivan('Алексей')
person2 = Ivan('Иван')
print(person1.name)
print(person2.name)

person2.surname = 'Петров'
```

### Результат.
![image](https://github.com/user-attachments/assets/729eaa0e-2923-45ae-b76f-492573f44c4e)


## Лабораторная работа №2
### Вам дали важное задание, написать продавцу мороженого программу,
которая будет писать добавили ли топпинг в мороженое и цену после
возможного изменения. Для этого вам нужно написать класс, в котором 
будет определяться изменили ли состав мороженого или нет. В этом
классе реализуйте метод, выводящий на печать «Мороженое с
{ТОППИНГ}» в случае наличия добавки, а иначе отобразится
следующая фраза: «Обычное мороженое». При этом программа должна
воспринимать как топпинг только атрибуты типа string.

```python
class Icecream:
    def __init__(self, ingredient=None):
        if isinstance(ingredient, str):
            self.ingredient = ingredient
        else:
            self.ingredient = None
            
            
    def composition(self):
        if self.ingredient:
            print(f"Мороженое с {self.ingredient}")
        else:
            print('Обычное мороженое')
            
            
icecream = Icecream()
icecream.composition()
icecream = Icecream('шоколадом')
icecream.composition()
icecream = Icecream(5)
icecream.composition()
```

### Результат.
![image](https://github.com/user-attachments/assets/d3fbafdd-e092-4216-a2c2-6c1c35115983)


## Лабораторная работа №3
### Петя – начинающий программист и на занятиях ему сказали реализовать
икапсу…что-то. А вы хороший друг Пети и ко всему прочему прекрасно
знаете, что икапсу…что-то – это инкапсуляция, поэтому решаете помочь
вашему другу с написанием класса с инкапсуляцией. Ваш класс будет не
просто инкапсуляцией, а классом с сеттером, геттером и деструктором.
После написания класса вам необходимо продемонстрировать что все
написанные вами функции работают.
Также вас необходимо объяснить Пете почему на скриншоте ниже в
консоли выводится ошибка.

```python
class MyClass:
    def __init__(self, value):
        self._value = value
        
    def set_value(self, value):
        self._value = value
        
    def get_value(self):
        return self._value 
    
    def del_value(self):
        del self._value 
        
    value = property(get_value, set_value, del_value, "Свойство value")
    
    
obj = MyClass(42)
print(obj.get_value())
obj.set_value(45)
print(obj.get_value())
obj.set_value(100)
print(obj.get_value())
obj.del_value()
# Ошибка в следующей строке:
print(obj.get_value())  # Ошибка: AttributeError, так как _value был удалён
```

### Результат.
![image](https://github.com/user-attachments/assets/2133dc62-6546-45db-9018-63d043504800)


## Лабораторная работа №4
### Вам прекрасно известно, что кошки и собаки являются
млекопитающими, но компьютер этого не понимает, поэтому вам нужно
написать три класса: Кошки, Собаки, Млекопитающие. И при помощи 
“наследования” объяснить компьютеру что кошки и собаки – это
млекопитающие. Также добавьте какой-нибудь свой атрибут для кошек
и собак, чтобы показать, что они чем-то отличаются друг от друга.

```python
class Mammal:
    className = 'Mammal'
    
    
class Dog(Mammal):
    species = 'canine'
    sounds = 'wow'
    weight = "1 kg - 40 kg"
    
    
class Cat(Mammal):
    species = 'feline'
    sounds = 'meow'
    weight = "2 kg - 30 kg"
    
    
dog = Dog()
print(f"Dog is {dog.className}, but they say {dog.sounds} and their weight is {dog.weight}")
cat = Cat()
print(f"Cat is {cat.className}, but they say {cat.sounds} and their weight is {cat.weight}")
```

### Результат.
![image](https://github.com/user-attachments/assets/f5b66b34-b57d-4e68-9e94-bc28683c3f6b)




## Лабораторная работа №5
### На разных языках здороваются по-разному, но суть остается
одинаковой, люди друг с другом здороваются. Давайте вместе с вами
реализуем программу с полиморфизмом, которая будет описывать всю
суть первого предложения задачи. Для этого мы можем выбрать два
языка, например, русский и английский и написать для них отдельные
классы, в которых будет в виде атрибута слово, которым здороваются на
этих языках. А также напишем функцию, которая будет выводить
информацию о том, как на этих языках здороваются.
Заметьте, что для решения поставленной задачи мы использовали
декоратор @staticmethod, поскольку нам не нужны обязательные
параметры-ссылки вроде self.

```python
class Russian:
    @staticmethod
    def greeting():
        print("Привет")
        
        
class English:
    @staticmethod
    def greeting():
        print("Hello")
        
        
def greet(language):
    language.greeting()
    
    
ivan = Russian()
greet(ivan)
john = English()
greet(john)
```

### Результат.
![image](https://github.com/user-attachments/assets/b5f52b5b-92d4-467b-b64e-c66e02379276)

## Самостоятельная работа №1
### Задание Садовник и помидоры.
Классовая структура:
Есть Помидор со следующими характеристиками:
• Индекс
• Стадия созревания (стадии: отсутствует, цветение, зеленый, красный)
Помидор может:
• Расти (переходить на следующую стадию созревания)
• Предоставлять информацию о своей зрелости
Есть Куст с помидорами, который:
• Содержит список томатов, которые на нем растут
А также может:
• Расти вместе с томатами
• Предоставлять информацию о зрелости всех томатов
• Предоставлять урожай
И также есть Садовник, который имеет:
• Имя
• Растение, за которым он ухаживает
Он может:
• Ухаживать за растением
• Собирать с него урожай
Задание:
Класс Tomato:
1) Создайте класс Tomato
2) Создайте статическое свойство states, которое будет содержать все
стадии созревания помидора
3) Создайте метод __init__(), внутри которого будут определены два
динамических свойства: _index (передается параметром) и _state (принимает первое значение из словаря states). После написания
этого блока кода в комментарии к нему укажите какими являются
эти два свойства
4) Создайте метод grow(), который будет переводить томат на
следующую стадию созревания
5) Создайте метод is_ripe(), который будет проверять, что томат созрел
Класс TomatoBush:
1) Создайте класс TomatoBush
2) Определите метод __init__(), который будет принимать в качестве
параметра количество томатов и на его основе будет создавать
список объектов класса Tomato. Данный список будет храниться
внутри динамического свойства tomatoes
3) Создайте метод grow_all(), который будет переводить все объекты
из списка томатов на следующий этап созревания
4) Создайте метод all_are_ripe(), который будет возвращать True, если
все томаты из списка стали спелыми.
5) Создайте метод give_away_all(), который будет чистить список
томатов после сбора урожая
Класс Gardener:
1) Создайте класс Gardener
2) Создайте метод __init__(), внутри которого будут определены два
динамических свойства: name (передается параметром, является
публичным) и _plant (принимает объект класса TomatoBush). После
написания этого блока кода в комментарии к нему укажите какими
являются эти два свойства
3) Создайте метод work(), который заставляет садовника работать, что
позволяет растению становиться более зрелым
4) Создайте метод harvest(), который проверяет, все ли плоды созрели.
Если все, то садовник собирает урожай. Если нет, то метод печатает
предупреждение
5) Создайте статический метод knowledge_base(), который выведет в
консоль справку по садоводству
Тесты:
1) Вызовите справку по садоводству
2) Создайте объекты классов TomatoBush и Gardener
3) Используя объект класса Gardener, поухаживайте за кустом с
помидорами
4) Попробуйте собрать урожай, когда томаты еще не дозрели.
Продолжайте ухаживать за ними
5) Соберите урожай
Результатом работы вашей программы будет листинг кода с подробными
комментариями и скриншоты выполенния всех тестов.

```python
class Tomato:
    # Статическое свойство stages с определением стадий созревания
    stages = ["отсутствует", "цветение", "зеленый", "красный"]

    def __init__(self, index):
        # Инициализация индекса и начальной стадии созревания
        self.index = index
        self.stage = self.stages[0]

    def grow(self):
        # Переводим томат на следующую стадию созревания
        current_stage = self.stages.index(self.stage)
        if current_stage < len(self.stages) - 1:
            self.stage = self.stages[current_stage + 1]

    def is_ripe(self):
        # Проверяем, созрел ли томат (стадия "красный")
        return self.stage == self.stages[-1]

    def __repr__(self):
        return f"Томат {self.index}: {self.stage}"


class TomatoBush:
    def __init__(self, count):
        # Создаем куст с заданным количеством помидоров
        self.tomatoes = [Tomato(i) for i in range(count)]

    def grow_all(self):
        # Заставляем все томаты расти
        for tomato in self.tomatoes:
            tomato.grow()

    def all_are_ripe(self):
        # Проверяем, что все томаты созрели
        return all(tomato.is_ripe() for tomato in self.tomatoes)

    def give_away_all(self):
        # Сбрасываем созревшие помидоры после сбора урожая
        self.tomatoes = []

    def __repr__(self):
        return "Куст: " + ", ".join(str(tomato) for tomato in self.tomatoes)


class Gardener:
    def __init__(self, name, plant):
        self.name = name  # Имя садовника
        self.plant = plant  # Растение, за которым он ухаживает

    def work(self):
        # Садовник ухаживает за растением, заставляя его расти
        print(f"{self.name} ухаживает за кустом с помидорами...")
        self.plant.grow_all()

    def harvest(self):
        # Проверка на созревание всех томатов перед сбором урожая
        if self.plant.all_are_ripe():
            print(f"{self.name} собрал урожай!")
            self.plant.give_away_all()
        else:
            print("Томаты еще не готовы к сбору!")

    @staticmethod
    def knowledge_base():
        # Справка для садоводов
        print("Справка:\n"
              "Томаты проходят стадии: отсутствует, цветение, зеленый, красный.\n"
              "Садовник ухаживает за кустом, пока томаты не созреют до красной стадии.")


# Тестирование
Gardener.knowledge_base()  # Вызов справки по садоводству

# Создание объектов TomatoBush и Gardener
bush = TomatoBush(4)  # Куст с 4 помидорами
gardener = Gardener("Петр", bush)

# Уход за кустом с помидорами
print(bush)
gardener.work()
print(bush)

# Попытка сбора урожая, когда томаты еще не дозрели
gardener.harvest()

# Продолжаем ухаживать за кустом
gardener.work()
print(bush)
gardener.work()
print(bush)

# Сбор урожая, когда все томаты созрели
gardener.harvest()
print(bush)

```

### Результат.
![image](https://github.com/user-attachments/assets/eed235d4-23e6-4dd5-b4e0-470848446de3)


### Вывод:
Эта задача помогает понять, как работает взаимодействие объектов в программировании. Я создал три класса — Tomato, TomatoBush и Gardener. Каждый класс выполняет свою задачу:
Tomato — описывает, как помидор проходит стадии созревания, от "отсутствует" до "красный".
TomatoBush — это куст, который содержит несколько помидоров и управляет их ростом.
Gardener — садовник, который ухаживает за кустом и собирает урожай, когда помидоры созреют.
Программа показала, как садовник может поэтапно ухаживать за кустом, пока все помидоры не созреют. Задача помогла закрепить понимание работы классов и объектов, а также их взаимодействие.

## Общие выводы по теме
Выполняя лабораторные и самостоятельные работы по ООП, я научился использовать главные принципы объектно-ориентированного программирования: инкапсуляцию, наследование и полиморфизм.
1. Инкапсуляция помогает прятать внутренние данные класса и управлять доступом к ним. Это делает код более защищенным и упрощает работу с данными.
2. Наследование позволяет создавать новые классы на основе уже существующих, что сокращает дублирование кода и упрощает его структуру.
3. Полиморфизм позволяет использовать одинаковые методы в разных классах, что делает код гибким и универсальным.
Эти задания помогли мне понять, как строить код, в котором классы работают вместе для выполнения задачи. Теперь я увереннее использую ООП для создания более структурированного и удобного кода.
