# Отчет по практической работе №2: Базовая 2D-игра «Инопланетное вторжение» 
# Выполнил студент ИВТ 2.2 Магер Е.В.

## **Цель работы**
Разработать 2D-игру «Инопланетное вторжение» с использованием библиотеки Pygame, где игрок управляет кораблём, уничтожая флот инопланетян. Основные задачи включают управление событиями, создание графики, анимации, взаимодействие объектов и реализацию игрового процесса.

---

## **Этапы выполнения**

### 1. **Настройка окружения**
- Установлена библиотека Pygame с помощью команды `pip install pygame`.
- Настроено рабочее окружение с использованием Python и Pygame.

---

### 2. **Создание игрового окна**
- В главном файле `alien_invasion.py` создано окно размером **1200x800 пикселей** с чёрным фоном.
- Использован метод `pygame.display.set_mode` для настройки экрана.
- Задано название окна игры: **"Alien Invasion"** через `pygame.display.set_caption`.

---

### 3. **Разработка основного цикла игры**
- Реализован главный цикл `while`, обеспечивающий:
  - Обработку событий (движение корабля, стрельба, выход из игры).
  - Обновление позиций корабля, пуль и инопланетян.
  - Перерисовку игрового экрана.
- Цикл завершает работу при выходе пользователя через `pygame.QUIT`.

---

### 4. **Класс Ship (Корабль)**
- Создан класс `Ship` в файле `ship.py` для управления игроком:
  - Задана стартовая позиция корабля в центре нижней границы экрана.
  - Реализовано управление движением вправо и влево через флаги `moving_right` и `moving_left`, обрабатываемые в методе `update`.
  - Корабль отображается методом `blitme`, который рисует изображение корабля на экране.

---

### 5. **Добавление стрельбы**
- Реализован класс `Bullet` в модуле `bullet.py`:
  - Снаряды создаются методом `_fire_bullet` в файле `alien_invasion.py`.
  - Пули движутся вверх с заданной скоростью и удаляются при выходе за верхнюю границу экрана.
  - Добавлено ограничение на количество снарядов, находящихся на экране одновременно (`bullets_allowed`).

---

### 6. **Создание флота инопланетян**
- Разработан класс `Alien` в модуле `alien.py`:
  - Инопланетянин создаётся с использованием изображения (`images/alien.bmp`) и позиционируется в начале экрана.
  - Реализован флот инопланетян с несколькими рядами и колоннами.
  - Флот движется горизонтально и изменяет направление при достижении края экрана. При этом он опускается вниз.
- Метод `_create_fleet` динамически рассчитывает количество инопланетян в зависимости от размера окна.

---

### 7. **Добавление конца игры и уровней**
- Реализована система жизней:
  - Количество жизней (`health`) уменьшается, если инопланетянин достигает нижней границы.
  - Игра завершается, если здоровье становится равным нулю.
- Добавлен переход на следующий уровень:
  - Уровень (`level`) увеличивается, если флот инопланетян уничтожен.
  - Сложность игры повышается с каждым уровнем за счёт увеличения скорости инопланетян.
- Отображение текущего состояния игры:
  - Количество здоровья, текущий счёт и уровень отображаются на экране.

---

### 8. **Организация структуры кода**
- Код разделён на модули для улучшения читаемости и удобства модификации:
  - **`alien_invasion.py`** — основной файл игры.
  - **`settings.py`** — хранит настройки игры (размер экрана, скорость, параметры пуль и инопланетян).
  - **`ship.py`** — отвечает за поведение корабля.
  - **`bullet.py`** — отвечает за снаряды.
  - **`alien.py`** — отвечает за создание и поведение инопланетян.
- Такое разделение позволяет легко модифицировать и расширять функциональность.

---

## **Реализованный функционал**

| Функционал                        | Реализация                                                                                  |
|-----------------------------------|--------------------------------------------------------------------------------------------|
| Управление кораблём               | Стрелки **влево** и **вправо** двигают корабль.                                            |
| Стрельба                          | Нажатие пробела выпускает снаряды.                                                        |
| Инопланетяне                      | Создан флот, который движется горизонтально и опускается вниз.                            |
| Конец игры                        | Игра завершается при столкновении инопланетян с кораблём или нижней границей экрана.      |
| Сохранение и загрузка             | Используются клавиши **S** и **L** для сохранения и загрузки прогресса.                   |
| Уровни сложности                  | При переходе на новый уровень скорость и сложность игры увеличиваются.                    |
| Система очков                     | Игрок получает очки за уничтожение инопланетян.                                           |
| Отображение состояния             | Отображаются текущие очки, уровень и здоровье.                                            |

---

## **Тестирование**
Игра была протестирована на базовых сценариях:
1. Движение корабля работает корректно: границы экрана не нарушаются.
2. Стрельба ограничена максимумом активных снарядов.
3. Инопланетяне корректно изменяют направление при достижении края экрана.
4. При столкновении пули с инопланетянином он исчезает, и начисляются очки.
5. Здоровье уменьшается при достижении инопланетянами нижней границы.
6. Переход на новый уровень работает: создаётся новый флот с увеличенной скоростью.

---

## **Заключение**
Практическая работа выполнена успешно. Создана базовая 2D-игра «Инопланетное вторжение» с функциональностью управления кораблём, стрельбы, системой очков, уровнями сложности и завершением игры. Код организован в модули для удобства чтения и модификации. 

Работа даёт практический опыт в использовании Pygame для создания игр, а также в реализации взаимодействий, графики и анимации.