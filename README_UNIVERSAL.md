# Wolf Tower Universal

Объединённая сборка исходников Wolf Tower: YouTube, Instagram и WhatsApp (включая WhatsApp Business). Это исходный проект, не готовые установщики.

## Состав
- Android-клиент на базе Wolf-Tower-YI.
- Desktop-клиент Windows/macOS на Electron.
- Общие профили и стратегии в `profiles/profiles.json`.
- Добавлена видимость пакетов WhatsApp и WhatsApp Business для Android 11+.

## Сборка Android
```bash
gradle -p android assembleDebug
```

## Сборка Windows и macOS
Готовые установщики собирает GitHub Actions: `.github/workflows/desktop.yml`. Вкладка Actions → запуск `Desktop build` → Artifacts (`WolfTower-windows` и `WolfTower-mac`). Локальный запуск требует собранный `ciadpi` в `desktop/resources/bin/<ОС>/`.

## Известные ограничения — прочитайте до установки
- **Это ещё не подтверждённый релиз.** Desktop-тесты проверяют логику, но нужна проверка на реальных Windows/macOS и Android-сетях.
- **Windows/macOS используют системный PAC-прокси, а не полноценный VPN.** Перехватываются только приложения, которые соблюдают системные настройки прокси. Нативные приложения WhatsApp для Windows/macOS этим способом не поддерживаются; используйте WhatsApp Web в браузере.
- **В текущем SOCKS5/DoH-переходнике UDP ASSOCIATE не реализован.** Сообщения WhatsApp по TCP могут работать с подходящей сетью и стратегией, но голосовые и видеозвонки через этот туннель не гарантируются.
- **Android-туннель пока IPv4-only.** Работа на мобильных сетях зависит от конкретного оператора и требует проверки при выключенном Wi-Fi. В проекте нет доказанного универсального исправления для всех сотовых сетей.
- WhatsApp не включён по умолчанию: включите его профиль в интерфейсе. Для Android приложение должно быть установлено (WhatsApp или WhatsApp Business).

## Проверки
В `desktop/` запустить `npm test`. Это не заменяет сборку и сетевые испытания. APK и установщики из этой копии не собраны.

## Лицензии
См. `third_party/LICENSES/` и лицензии сторонних библиотек.
