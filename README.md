# Тема 8. Введение в ООП
Отчет по Теме #8 выполнил(а):
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
### Создайте класс “Car” с атрибутами производитель и модель. Создайте
объект этого класса. Напишите комментарии для кода, объясняющие
его работу. Результатом выполнения задания будет листинг кода с
комментариями.

```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model


my_car = Car("Toyota", "Corolla")
```

## Лабораторная работа №2
### Дополните код из первого задания, добавив в него атрибуты и методы
класса, заставьте машину “поехать”. Напишите комментарии для кода,
объясняющие его работу. Результатом выполнения задания будет
листинг кода с комментариями и получившийся вывод в консоль.

```python
class Car:

    def __init__(self, make, model):
        self.make = make
        self.model = model 


    def drive(self):
        print(f"Driving the {self.make} {self.model}")
        

my_car = Car("Toyota", "Corolla")

my_car.drive()
```

### Результат.
![image](https://github.com/user-attachments/assets/960292e3-7f18-4735-a431-7ad99c7abaca)


## Лабораторная работа №3
### Создайте новый класс “ElectricCar” с методом “charge” и атрибутом
емкость батареи. Реализуйте его наследование от класса, созданного в
первом задании. Заставьте машину поехать, а потом заряжаться.
Напишите комментарии для кода, объясняющие его работу.
Результатом выполнения задания будет листинг кода с комментариями
и получившийся вывод в консоль.

```python
class Car:

    def __init__(self, make, model):
        self.make = make 
        self.model = model  

    def drive(self):
        print(f"Driving the {self.make} {self.model}")  


my_car = Car("Toyota", "Corolla")

my_car.drive()


class ElectricCar(Car):

    def __init__(self, make, model, battery_capacity):

        super().__init__(make, model)
        self.battery_capacity = battery_capacity 


    def charge(self):
        print(f"Charging the {self.make} {self.model} with {self.battery_capacity} kWh") 


my_electric_car = ElectricCar("Tesla", "Model S", 75)

my_electric_car.drive()

my_electric_car.charge()
```

### Результат.
![image](https://github.com/user-attachments/assets/7de0e2b5-465b-4fe2-9cd0-c4513b3cd039)


## Лабораторная работа №4
### Реализуйте инкапсуляцию для класса, созданного в первом задании.
Создайте защищенный атрибут производителя и приватный атрибут
модели. Вызовите защищенный атрибут и заставьте машину поехать.
Напишите комментарии для кода, объясняющие его работу.
Результатом выполнения задания будет листинг кода с комментариями
и получившийся вывод в консоль.

```python
class Car:
    
    def __init__(self, make, model):
        self._make = make  
        self.__model = model  
        
    
    def drive(self):
        print(f"Driving the {self._make} {self.__model}")  
        

my_car = Car("Toyota", "Corolla")


print(my_car._make) 

my_car.drive()

```

### Результат.
![image](https://github.com/user-attachments/assets/67761101-11d4-47f1-a5ec-6cab0341743b)


## Лабораторная работа №5
### Реализуйте полиморфизм создав основной (общий) класс “Shape”, а
также еще два класса “Rectangle” и “Circle”. Внутри последних двух
классов реализуйте методы для подсчета площади фигуры. После этого
создайте массив с фигурами, поместите туда круг и прямоугольник,
затем при помощи цикла выведите их площади. Напишите
комментарии для кода, объясняющие его работу. Результатом
выполнения задания будет листинг кода с комментариями и
получившийся вывод в консоль.

```python
class Shape:
 
    def area(self):
        pass


class Rectangle(Shape):
  
    def __init__(self, width, height):
        self.width = width  
        self.height = height  


    def area(self):
        return self.width * self.height  


class Circle(Shape):
   
    def __init__(self, radius):
        self.radius = radius  
        
    
    def area(self):
        return 3.14 * self.radius * self.radius  


shapes = [Rectangle(5, 4), Circle(3)]

for shape in shapes:
    print(shape.area())
```

### Результат.
![image](https://github.com/user-attachments/assets/f7b94f94-379f-46db-bc01-432af923b922)


## Самостоятельная работа №1
### Самостоятельно создайте класс и его объект. Они должны
отличаться, от тех, что указаны в теоретическом материале
(методичке) и лабораторных заданиях. Результатом выполнения
задания будет листинг кода и получившийся вывод консоли

```python
class Animal:
    def __init__(self, name, species):
        self.name = name
        self.species = species

    def info(self):
        return f"{self.name} принадлежит к виду {self.species}."


dog = Animal("Шарик", "собака")
print(dog.info())

```

### Результат.
![image](https://github.com/user-attachments/assets/ac02c125-a331-4415-b9ca-cd6fd858e6ab)

### Вывод
Программа успешно создаёт класс Animal с двумя атрибутами и выводит информацию об объекте. Класс и объект созданы корректно.

## Самостоятельная работа №2
### Самостоятельно создайте атрибуты и методы для ранее созданного
класса. Они должны отличаться, от тех, что указаны в
теоретическом материале (методичке) и лабораторных заданиях.
Результатом выполнения задания будет листинг кода и
получившийся вывод консоли

```python
class Animal:
    def __init__(self, name, species, age):
        self.name = name
        self.species = species
        self.age = age

    def info(self):
        return f"{self.name} принадлежит к виду {self.species} и ему(ей) {self.age} лет."


cat = Animal("Барсик", "кошка", 5)
print(cat.info())

```

### Результат.
![image](https://github.com/user-attachments/assets/d06871e0-67ee-4148-8042-9430d500450a)

### Вывод
Программа добавляет новый атрибут age и изменяет метод info для отображения возраста. Атрибуты и методы успешно добавлены.

## Самостоятельная работа №3
### Самостоятельно реализуйте наследование, продолжая работать с
ранее созданным классом. Оно должно отличаться, от того, что
указано в теоретическом материале (методичке) и лабораторных
заданиях. Результатом выполнения задания будет листинг кода и
получившийся вывод консоли

```python
class Animal:
    def __init__(self, name, species):
        self.name = name
        self.species = species

    def info(self):
        return f"{self.name} принадлежит к виду {self.species}."


class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name, "собака")
        self.breed = breed

    def bark(self):
        return f"{self.name} из породы {self.breed} лает."


dog = Dog("Рекс", "овчарка")
print(dog.info())
print(dog.bark())

```

### Результат.
![image](https://github.com/user-attachments/assets/cb87639a-71dc-40f9-886e-533ff1975596)

### Вывод
Программа использует наследование для создания класса Dog, который наследует от Animal. Добавлен метод bark. Наследование реализовано корректно.

## Самостоятельная работа №4
### Самостоятельно реализуйте инкапсуляцию, продолжая работать с
ранее созданным классом. Она должна отличаться, от того, что
указана в теоретическом материале (методичке) и лабораторных
заданиях. Результатом выполнения задания будет листинг кода и
получившийся вывод консоли.

```python
class Animal:
    def __init__(self, name, species):
        self.__name = name
        self.species = species

    def set_name(self, name):
        self.__name = name

    def get_name(self):
        return self.__name

    def info(self):
        return f"{self.__name} принадлежит к виду {self.species}."


dog = Animal("Бобик", "собака")
print(dog.info())
dog.set_name("Барбос")
print(dog.info())

```

### Результат.
![image](https://github.com/user-attachments/assets/f4df3313-4205-4b39-b7b5-fd4497501c16)

### Вывод
Программа использует инкапсуляцию, защищая атрибут name и добавляя методы для его изменения. Программа работает корректно: инкапсуляция реализована, доступ к атрибуту контролируется через методы.

## Самостоятельная работа №5
### Самостоятельно реализуйте полиморфизм. Он должен отличаться,
от того, что указан в теоретическом материале (методичке) и
лабораторных заданиях. Результатом выполнения задания будет
листинг кода и получившийся вывод консоли.

```python
class Animal:
    def sound(self):
        raise NotImplementedError("Должен быть реализован метод в подклассе")


class Dog(Animal):
    def sound(self):
        return "Гав-гав"


class Cat(Animal):
    def sound(self):
        return "Мяу-мяу"


animals = [Dog(), Cat()]
for animal in animals:
    print(animal.sound())

```

### Результат.
![image](https://github.com/user-attachments/assets/1a8125fb-f65c-4f37-99a2-e277791b834e)

### Вывод
Программа реализует полиморфизм через метод sound в классах Dog и Cat. Полиморфизм реализован корректно, объекты ведут себя по-разному в зависимости от класса.

## Общий вывод
Выполнив эту лабораторную работу, я научился основам объектно-ориентированного программирования (ООП) на практике. Я освоил такие важные концепции, как создание классов и объектов, работа с атрибутами и методами, использование наследования для создания дочерних классов, инкапсуляция данных для защиты атрибутов, а также реализация полиморфизма для изменения поведения объектов на основе их классов. Эти навыки помогут мне лучше организовывать код и делать программы более гибкими и модульными, что является ключевым аспектом современного программирования.
