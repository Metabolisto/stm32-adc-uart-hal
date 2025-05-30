# STM32 ADC + UART (HAL) Example

 Простой пример проекта на STM32, демонстрирующий чтение аналогового сигнала через ADC и передачу данных по UART с использованием HAL.

## 🛠 Платформа и инструменты

-  **MCU:** STM32F103C8T6 ("Blue Pill")
-  **Среда разработки:** STM32CubeIDE
-  **Библиотеки:** STM32 HAL (CubeMX)
-  **Отладка:** ST-Link V2

##  Описание проекта

Проект выполняет следующие функции:

1. Настраивает **ADC** на один канал в непрерывном режиме.
2. Использует **UART** для отправки результатов преобразования на ПК (через USB-UART CH340G).
3. Передача выполняется в текстовом виде, с задержкой.

## Структура проекта
```
ADC_UART_HAL/
├── Core/                  # Исходники и заголовки проекта
│   ├── Inc/               # Заголовочные файлы (.h)
│   └── Src/               # Исходные файлы (.c)
├── Drivers/               # Драйверы STM32 HAL
├── .gitignore             # Исключения Git
├── README.md              # Документация
├── STM32CubeIDE/          # Конфигурация IDE и .project файлы
└── .ioc                   # STM32CubeMX файл конфигурации
```
## ⚙️ Подключение
```
STM32F103C8T6 ("Blue Pill"):

**PA1 (ADC1_IN1)** — аналоговый вход (подключаем к +3.3v через потенциометр 10КОм)
**PA9 (TX)** — UART передача
**PA10 (RX)** — UART приём *(не используется)*

Преобразователь USB-UART CH340G:
TX и GND USB-UART адаптера к PA9 и GND Blue Pill
```
- [Монтажная схема](https:github.com/Metabolisto/stm32-adc-uart-hal/blob/main/assets/Fritzing_diagram.png)
- [Подключение ST-LINK V2](https:github.com/Metabolisto/stm32-adc-uart-hal/blob/main/assets/ST-LINK_V2.jpg)
- [Подключение USB-UART CH340G](https:github.com/Metabolisto/stm32-adc-uart-hal/blob/main/assets/USB-UART_CH340G.jpg)

## Конфигурация (из CubeMX)

| Периферия | Параметры               |
|-----------|-------------------------|
| ADC1      | Single channel, Polling |
| UART1     | 115200 baud, 8N1        |

- [Конфигурация в CubeMX](https:github.com/Metabolisto/stm32-adc-uart-hal/blob/main/assets/CubeMX_Configuration.jpg)

## Зависимости

Проект не использует внешние библиотеки кроме STM32 HAL.

## Как прошить

1. Открыть проект в STM32CubeIDE.
2. Собрать (`Ctrl + B`).
3. Подключить ST-Link и прошить (`Run → Debug` / `Ctrl + F11`).
4. Подключить преобразователь USB-UART CH340G
5. Открыть любой терминал (я использовал UART Assistant) на скорости 115200 бод, 8 датабит, 1 стопбит и наблюдать значения.

## Связанные проекты

- [STM32 DHT11 UART](https:github.com/Metabolisto/stm32-dht11-uart) 