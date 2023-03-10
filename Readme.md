## Ветка решения по Задаче 2

# XML, JSON, CSV

## Задача 1 (обязательная)

:warning: Эта задача является продолжением [задачи про сериализацию](./SERIAL.md), поэтому для выполнения этой лучше сперва нужно получить по ней зачёт.

Возьмите репо с решением [задачи про сериализацию](./SERIAL.md) и отведите новую ветку `json` от `main`.

Создайте класс `ClientLog` для сохранения всех операций, которые ввёл пользователь.
Т.е. покупатель добавил покупку, то это действие должно быть там сохранено. Для этого создайте там метод `log(int productNum, int amount)`.
Также у объекта этого класса должен быть метод `exportAsCSV(File txtFile)` для сохранения всего журнала действия в файл в формате csv.
Пример файла который должен получиться:
```csv
productNum,amount
3,4
1,1
3,2
5,12
```

В конце работы программы сохраняйте журнал действий в файл `log.csv`.

Также вместо вызова метода `saveTxt` в методе `main` сериализуйте корзину в json-формате в файл `basket.json`.
Аналогично при старте программы загружайте корзину десериализацией из json-а из файла `basket.json`, а не из обычной текстовой сериализации как было до того.
При этом логику сериализации в методах в классе корзины трогать не нужно.

Коммит и пуш в ветку `json`.

## Задача 2 (обязательная)

Эту задачу делайте в том же репозитории и ветке, что и первую.

В корне вашего проекта разместите: `shop.xml` с содержимым:
```xml
<config>
  <load>
    <enabled>false</enabled>
    <fileName>basket.json</fileName>
    <format>json</format>
  </load>
  
  <save>
    <enabled>true</enabled>
    <fileName>basket.json</fileName>
    <format>json</format>
  </save>
  
  <log>
    <enabled>true</enabled>
    <fileName>client.csv</fileName>
  </log>
</config>
```

При старте ваша программа должна считывать этот файл и загружать из него настройки:
* блок `load` говорит нужно ли загружать данные корзины при старте программы из файла (`enabled`), указывает имя этого файла (`fileName`) и формат (`json` или `text`). Ваша программа должна вести себя соответствующим образом.
* блок `save` говорит нужно ли сохранять данные корзины после каждого ввода, куда и в каком формате (`text` или `json`).
* блок `log` говорит нужно ли сохранять лог при завершении программы и в какой файл; формат лога всегда csv.

Сделайте коммит и пуш в ветку `json`.
