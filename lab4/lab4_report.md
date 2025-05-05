Приложение: Telegram-бот, который по текстовому промпту генерирует изображение в стилях Ghibli Art, Realistic и Pixel Art, и возвращает его пользователю.

Флоу приложения:
![flow drawio](https://github.com/user-attachments/assets/6343241f-9796-4d53-b065-c6214ea28904)

Начальная разработка

Схема инфраструктуры:

![infra drawio](https://github.com/user-attachments/assets/dd2eb867-0aee-4eff-8dc7-23e6b48db7a3)

Стоимость:

<img width="442" alt="Screenshot 2025-05-05 at 18 46 16" src="https://github.com/user-attachments/assets/56d410ca-b754-45b2-a8de-a135d4669316" />

Обоснование:
- Cloud Run: мгновенный деплой контейнера, авто-масштабирование при загрузке и 0$ при простое.
- Cloud Storage: дешёвое и долговечное хранение сгенерированных изображений.
- Firestore: хранение метаданных (промпт, стиль, ссылка на картинку)

Тестирование партнёрами:

Схема инфраструктуры:

![infra_testing drawio](https://github.com/user-attachments/assets/ce377de4-c3b3-441e-9fd1-ceee5b20e67a)

Стоимость:

<img width="506" alt="Screenshot 2025-05-05 at 18 59 08" src="https://github.com/user-attachments/assets/cb4cd9b2-8392-4975-8842-8a6cef6a4f2b" />

Обоснование:
- Load Balancer обеспечивает равномерное распределение нагрузки между репликами.
- Monitoring/Logging необходимы для диагностики производительности и ошибок.
- Ресурсы увеличены, чтобы выдержать возросший трафик тестировщиков

Продовое решение

Схема инфраструктуры:

![infra_prod drawio](https://github.com/user-attachments/assets/c1096b47-c00a-4816-91ce-cf1fa31ccb35)

Стоимость:

<img width="507" alt="Screenshot 2025-05-05 at 19 16 18" src="https://github.com/user-attachments/assets/050bc30e-4753-438d-aca3-88ade5a6e651" />

Обоснование:
- GKE: гарантированная отказоустойчивость, гибкий автоскейл на пике нагрузки.
- Cloud SQL: реляционная БД для сложных запросов и аналитики.
- Cloud Armor: защита от DDoS и правил безопасности.

Выводы:
- На старте минимизируем расходы, используя безсерверные сервисы.
- На этапе тестирования добавляем балансировку и мониторинг для стабильности на пике.
- В продакшне переходим к Kubernetes и реляционной БД для высокой доступности и гибкости.
