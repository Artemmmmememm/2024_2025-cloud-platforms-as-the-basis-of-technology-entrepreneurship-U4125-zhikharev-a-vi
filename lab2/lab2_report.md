Шаг №1. Зайдем в Cloud Run на Google Cloud Platform и нажмем на Deploy. Используем существующий сервис hello и выставим минимальные настройки сервиса. Установим 8080 порт. Дадим доступ неавторизованным пользователям. Проверим, что сервис запущен, перейдя по созданной ссылке
![image](https://github.com/user-attachments/assets/72891e21-5941-4cc9-a7e6-b3ac45759d02)

Шаг №2. Проверим текущие Логи и Метрики
![telegram-cloud-photo-size-2-5206333762957339468-y](https://github.com/user-attachments/assets/f7e71262-5098-4a4b-b304-3b45aa87582c)
![telegram-cloud-photo-size-2-5206333762957339480-y](https://github.com/user-attachments/assets/c2b1b8e9-d38c-4c11-a7c5-f75930246716)

Шаг №3. Изменим порт на 8090 и изменим траффик
![telegram-cloud-photo-size-2-5206333762957339482-y](https://github.com/user-attachments/assets/ddb042d2-fbea-4cb2-9736-25430912e1c0)
![telegram-cloud-photo-size-2-5206401584785913798-y](https://github.com/user-attachments/assets/91e6d138-1f4f-4697-9ebf-011392a5e75b)

Ша №4. Рассмотрим изменения в метриках и логах
![telegram-cloud-photo-size-2-5206401584785913822-y](https://github.com/user-attachments/assets/4c4d3492-bdbc-493c-b212-19bcc26910c1)
- В логах видно, что контейнер теперь запускается и слушает порт 8090 вместо 8080.
- Произошло обновление сервиса (ReplaceService), после чего контейнер выводит сообщение о старте на новом порту.
- Container Instance Count: наблюдался всплеск до двух активных экземпляров во время переключения.
- CPU/Memory Utilization: минимальные нагрузки, стабильные показатели (CPU около 1%, память около 10-20%).
- Container Startup Latency: небольшая задержка старта контейнера (примерно 80 мс).
- Max Concurrent Requests: максимум 2 одновременных запроса во время переключения.

Шаг №5. Удалим Cloud Run


