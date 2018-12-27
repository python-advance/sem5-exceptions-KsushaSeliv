# sem5-exceptions
Самостоятельная работа (ИСР, ВСР)

<h1>Инвариантная работа</h1>
1.1. Разработать программу с реализацией функции для считывания json- данных из файла и вывод их в табличном виде на экран. Реализовать базовый синтаксис для обработки исключений (try .. except)
1.2. Дополнение программы для считывания данных проверкой утверждений или высказываний (assert). Создание отдельного блока для такой проверки (с помощью __name__) и скрипта командной строки для запуска этих проверок.
1.3. Дополнение программы для считывания данных с использованием менеджера контекстов и реализации расширенного синтаксиса для обработки исключений.

import json #модуль json позволяет кодировать и декодировать данные в удобном формате
from prettytable import PrettyTable #используем библиотеку Pretty Table для создания таблицы с идентификатороми

```python
Guest_book ='file1.json'

def openguest (Guest_book):



  try:
        file_book = open(Guest_book, 'r') #типо открываем файл для чтения
        data = json.loads(file_book.read()) #типо загружаем данные из файла json в data
  except FileNotFoundError: #поднимаем исключение
        print ("Файл не был найден.")



  with open(Guest_book, 'r') as f: #вот тут открываем и загружаем
     data = json.loads(f.read())

  name = []
  surname = []


#Здесь должен быть кусок кода, но, к сожалению, пока его нет, потому что нет идей
  
  table = PrettyTable()
  table.add_column(names, 'guests_name') 
  table.add_column(surname, 'guests_surname')
  print(table)

read('file1.json')
```

<h1>Вариантная работа</h1>
1.3. Создание программы для считывания данных формата CSV c использованием функционала модуля contextlib.
```python
import requests
from contextlib import closing
import csv

url = "http://download-and-process-csv-efficiently/python.csv"

with closing(requests.get(url, stream=True)) as r:
    reader = csv.reader(r.iter_lines(), delimiter=',', quotechar='"')
    for row in reader:
        print row   
```
#Установив stream=True в запросе GET, когда мы передаем r.iter_lines() в csv.reader (), мы передаем генератор в csv.reader (). Поступая #таким образом, мы разрешаем csv.reader () лениво перебирать по каждой строке ответа for row in reader .

#Это позволяет избежать загрузки всего файла в память, прежде чем мы начнем его обрабатывать, что резко сократит объем памяти для #больших файлов .






