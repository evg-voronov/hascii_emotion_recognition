<p align="center">
  <img src="screenshot/hello..png"/></div>
</p>

Surface
-------
**Surface** — это приложение, разработанное командой hello, которое способно облегчить процесс реабилитации людей, переживших инсульт.  С помощью web камеры пользователь сможет в режиме реального времени выполнять упражнения и восстанавливать нормальную подвижность мимических мышц. В отличие от обычного зеркала наше приложение способно идентифицировать мимические мышцы и следить за ними, а также определять эмоции.

### Surface работает в двух режимах. 

**Первый режим** — это выполнение упражнений. К программе предоставляется документация базовых заданий (word документ "Упражнения" в корневом каталоге), которые необходимо выполнять для восстановление мышц лица, в процессе выполнения упражнений на лице отображаются контрольные точки с помощью, которых в будущем планируется вести мониторинг прогресса (следить за изменением подвижность мышц вычисляя координаты точки).

<p align="center">
  <img src="screenshot/key_points.png"/></div>
</p>

**Второй режим** — это проверка на способность корректно выражать эмоции. Программа с помощью нейронной сети способно детектировать 7 базовых эмоций (радость, удивление, грусть, злость, отвращение, страх, нейтральная эмоция) и выводить результат на экран в виде процентной вероятности. Также к программе предоставляется документация по тому, как правильно следует выражать конкретную эмоцию (word документ "Эмоции" в корневом каталоге).

<p align="center">
  <img src="screenshot/emotion.png"/></div>
</p>

## Описание

Приложение состоит из двух несвязанных частей.

С помощью первой части производятся исследование на точность распознования 2х детекторов лиц метода Виолы-Джонса и истограммы направленных градиентов (Histograms of Oriented Gradients - HOG).

**test-find-face-photo.py** — с помощью данного скрипта тестируется работа двух детекторов лиц (Виолы Джонсна и hog) на фотографиях людей с инсультом. Данный скрипт был создан для проверки 2х алгоритмов на способность детектировать лица с инсультом.

**test-find-face-video.py** — Проверка на количество пропущенных кадров с лицами в видео потоке. Тестирование показало, что HOG немного точнее (41% неопредленных кадров против 49% у метода Виолы-Джонса).

Вторая часть это само приложение с графическим интерфейсом для пользователей.

**find-face-video.py** — скрипт приложения которое определяет лицо и ключевые точки.

**emotion_video.py** — скрипт с функциями по опредлению эмоций на изображениях.

**neural_network.py** — скрипт нейронной сети.

**form_fon.py** — пользовательский интерфейс, написанный с помощью библиотеки PyQt5 (именно тот файл, который нужно запускать).

С помощью интерфейса вы можете включить режим зеркала (просто запись с web камеры), включить отображение ключевых точек для выполнения упражнений или режим распознавания эмоций. Также есть возможность поставить трансляцию на паузу.

## Установка 

Если вы используете windows, то прежде, чем установить dlib необходимо установить следующие компоненты

`Visual Studio 2015`

`CMake v3.8.2`

`Anaconda 3`

Если вы используете Linux

sudo apt-get install build-essential cmake
sudo apt-get install libgtk-3-dev
sudo apt-get install libboost-all-dev

pip install dlib==19.20.0

Также необходимо скачать файлы нейронной сети в корень каталога программы 

https://drive.google.com/open?id=1-nrr8RoJLvX6v-OblMLLGVicNean0yqE
