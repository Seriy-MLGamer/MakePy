<!--
MIT Expat license

(C) 2025 Серый MLGamer <Seriy-MLGamer@yandex.ru>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
-->

# MakePy

Продвинутая сборка исходного кода &mdash; просто, как в пакетном менеджере.

	python make.py build revolution

*Революция в сфере управления исходным кодом!* **MakePy** &mdash; это *свободный* каркас для языка Python, с помощью которого вы можете производить широкий спектр операций с вашим исходным кодом и другими файлами на различных операционных системах и процессорных архитектурах. Отличная альтернатива программам Make, CMake и подобным.

## Преимущества

### Сила Питона!

Сценарий сборки программируется на языке **Python** &mdash; Тьюринг-полноценном языке программирования общего назначения, позволяющем программировать в процедурном, функциональном, объектно-ориентированном и других стилях. *Больше не возникнет задач, которые сложно или невозможно решить с помощью собственных языков программирования известных программ сборки.*

### Полный цикл сборки

С помощью **всего одной команды** производится полный цикл сборки: от компиляции исходного кода до упаковки пакетов. *Достигается высокий уровень автоматизации.*

### Удобный интерфейс

Интерфейс командной строки тоже может быть **удобным**. *Опыт использования данной системы сборки напоминает пакетный менеджер.* Цели сборки делятся на пути (файлы и папки) и пакеты. Сначала указывается действие, выполняемое над путями и пакетами, а затем перечисляются пути и пакеты.

	./make.py [действие] {<путь или пакет>|path:<путь>|package:<пакет>} [...]

### Система, которую можно подстроить под себя

Каркас является **объектно-ориентированным**. *На основе имеющихся классов можно создавать свои с самыми разными содержанием и поведением.* Можно использовать как встроенный инструментарий, так и добавленный самостоятельно. Можно добавлять свои действия и свои типы целей.

## Встроенный функционал

  * Создание папок
  * Автоматическое добавление целей для автоматического создания папок
  * Создание символьных ссылок
  * Компиляция объектных файлов
  * Сборка исполняемых файлов
  * Сборка статических библиотек
  * Сборка разделяемых библиотек
  * Генерация статических интерфейсов для разделяемых библиотек &laquo;.dll&raquo;
  * Извлечение списков символов (&laquo;.def&raquo;-файл) из разделяемых библиотек &laquo;.dll&raquo;
  * Очистка рабочей папки от сгенерированных файлов и папок с автоматическим определением удаляемых файлов и папок
  * Установка файлов и папок с предварительной установкой пакетов-зависимостей
  * Удаление установленных файлов и папок с автоматическим определением удаляемых файлов, папок и зависимых пакетов
  * Упаковка сгенерированных файлов и папок в архив или пакет

На данный момент встроенный функционал каркаса поддерживает языки программирования C и C++, компиляторы GCC и Clang и операционные системы GNU/Linux и Windows. Возможно упаковать пакет Debian (&laquo;.deb&raquo;) на дистрибутиве GNU/Linux, основанном на Debian, с помощью инструментов пакета `debhelper` (также нужно использовать файл &laquo;sample debian rules&raquo;, находящийся в репозитории, в качестве файла &laquo;debian/rules&raquo;).

## Использование

Добавляем файл &laquo;makepy.py&raquo; из репозитория в папку вашего проекта или в папку с модулями Python.

Создаём в папке проекта сценарий сборки и называем его, например, &laquo;make.py&raquo;.

### Пример сценария сборки

	#!/usr/bin/python3 -B
	
	from makepy import *
	
	class Hello_Revolution(MakePy):
		def main(self, defines):
			Package(self, "build", "revolution", {"build": Dependencies([self.executable("revolution")])})
			Executable_C(self, "revolution", "main.o")
			Object_C(self, "main.c")
			Clean(self, "revolution")
	Hello_Revolution("revolution", "build", "package").make()

Запускаем сценарий сборки.

#### Bash

	$ ./make.py

#### CMD

	>python make.py

### Дерево проекта до запуска

	src
	  main.c
	make.py
	makepy.py

### Дерево проекта после запуска

	bin
	  revolution{.exe}
	obj
	  main.o
	src
	  main.c
	make.py
	makepy.py

Для подробного ознакомления с каркасом введите следующие команды:

#### Консоль Python

	>>> import makepy
	>>> help(makepy)

А также введите команду:

#### Bash

	$ ./make.py --help

#### CMD

	>python make.py --help

*Сборка программы из исходного кода должна быть доступной для пользователя.*

Вы тоже так считаете? Тогда используйте **MakePy**!

# Дальнейшее развитие

Определённо, это ещё не предел совершенства. Вот список вещей, которые ещё предстоит добавить.

  1. Более подробная документация
  2. Улучшение стабильности и безопасности использования
  3. Улучшение восприятия кода сценария сборки
  4. Многопоточность
  5. Шкала прогресса
  6. Поддержка других компиляторов
  7. Поддержка других языков программирования
  8. Поддержка других операционных систем
  9. Упаковка пакетов других типов
  10. Анализ исходного кода (автоматическое определение зависимостей)
  11. Обратная совместимость
  12. Добавление в репозиторий PyPI
  13. Мало ли что ещё