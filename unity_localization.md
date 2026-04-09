# Локализация игры на Unity: DoubleShake Beta

## Инструменты
- Visual Studio Code
- FontForge
- Uabea
- dnSpy
- HxD
- Windows PowerShell

## Исходная структура папки с игрой
```
DoubleShake_Data/
├── Managed/
├── Resources/
├── StreamingAssets/
│   ├── textpack_eng.json
│   ├── textpack_eng2.json
│   └── textpack_pir.json
├── app.info
├── boot.config
├── globalgamemanagers
├── globalgamemanagers.assets
├── level0
├── level1
├── level2
├── level2.resS
├── level3
├── resources.assets
├── resources.assets.resS
├── RuntimeInitializeOnLoads.json
├── ScriptingAssemblies.json
├── sharedassets0.assets
├── sharedassets0.assets.resS
├── sharedassets0.resource
├── sharedassets1.assets
├── sharedassets2.assets
├── sharedassets2.assets.resS
├── sharedassets3.assets
└── sharedassets3.assets.resS
```

### Анализ структуры

Приоритет определялся по трудоёмкости: от простого к сложному.

| Файл | Что содержит | Как было извлечено | Инструмент |
|------|--------------|---------------|------------|
| `StreamingAssets/*.json` | Диалоги, основной текст | прямое редактирование | VS Code |
| `sharedassets2.assets` | Текст в текстурах (логотипы, заголовки) | экспорт .png → редактирование в графическом редакторе → импорт .png | UABEA + Photoshop |
| `sharedassets1.assets` | Шрифты (не было кириллицы) | экспорт шрифта → добавление глифов → импорт шрифта | FontForge + UABEA |
| `Managed/Assembly-CSharp.dll` | Строки в скомпилированном коде | декомпиляция → поиск → шестнадцатеричная замена или замена IL | dnSpy + HxD |

### Особые случаи

#### Отсутствие кириллицы в шрифтах
Шрифты не содержали русских букв. Через FontForge добавлены недостающие глифы, шрифт пересобран и заменён в `.assets`.


