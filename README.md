# Welcome to Expo Map app with DB👋

## Инструкция по установке
1. Клонируйте репозиторий:
   ```bash
   git clone https://github.com/0LD-CAT/ExpoMapApp.git
   ```

2. Установите зависимости.
   ```bash
   npm install
   ```

3. Запустите приложение.
   ```bash
   npx expo start
   ```

4. Отсканируйте qr-code в приложении Expo Go.

## Документация схемы базы данных
        `CREATE TABLE IF NOT EXISTS markers (
          id INTEGER PRIMARY KEY AUTOINCREMENT,
          latitude REAL NOT NULL,
          longitude REAL NOT NULL,
          title CHAR NOT NULL,
          description TEXT,
          created_at DATETIME DEFAULT CURRENT_TIMESTAMP
        );`

        `CREATE TABLE IF NOT EXISTS marker_images (
          id INTEGER PRIMARY KEY AUTOINCREMENT,
          marker_id INTEGER NOT NULL,
          uri TEXT NOT NULL,
          created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
          FOREIGN KEY (marker_id) REFERENCES markers (id) ON DELETE CASCADE
        );`

## Описание подхода к обработке ошибок
- При загрузке карты происходит инициализация БД, создание таблиц(если не созданы) и чтение информации маркеров.
- При выполнении операций происходит проверка на инициализацию БД и вывод подробной ошибки в консоль.
