# Учебный комплект практики 3.6 «Интеграция ML»: данные + приложение Qlik (трек BI-аналитика)

Датасет и приложение Qkik для визуального анализа качества ML-модели на
карточках инцидентов SOC. Данные учебные (условные); сценарии
сформированы для занятий курса «Интеллектуальный анализ и визуализация
данных».

## 1. Состав комплекта

```
iavd_incidents_raw3_field_dictionary.md  — словарь полей
README.md                              — этот файл
Qlik\
  Apps\IAVD_Assessment_v01.qvf                    — приложение Qlik Sense
  Scripts\IAVD_Assesment_Script_v02_annotated.qvs — скрипт с комментариями
  Png\IAVD_Assesment_View1.png, View2.png        — лист в режиме просмотра
  Png\IAVD_Assesment_Edit.png                    — лист в режиме редактирования
  Png\IAVD_Assesment_DM.png                      — модель данных
  Data\3\Parquet\Gen\iavd_incidents_raw3_target.parquet   — карточки (16 443)
  Data\3\Parquet\Gen\MODEL_PREDICTIONS_target.parquet     — инференс ML (19 393)
  Data\3\Parquet\Gen\calendar.parquet                     — справочник дат
  Data\3\Parquet\Gen\dataframe.parquet                    — «Период» (окна)
```

## 2. Порядок работы

1. Распакуйте комплект так, чтобы каталог `Qlik` (внутри `source`)    сохранил имя и структуру.
2. Скопируйте `Apps\IAVD_Assessment_v01.qvf` в папку  C:\Users\...\Documents\Qlik\Sense\Apps`. Откройте приложение.
3. (Рекомендуется) Откройте «Data load editor» и создайте файловое подключение с именем **`RootIAVD`**,   указав его на каталог-РОДИТЕЛЬ каталога `Qlik` (скрипт обращается к   данным как `lib://RootIAVD/Qlik/Data/3/...`).  Перезагрузите приложение («Reload»). Данные — четыре    parquet-файла из `Data\3\Parquet\Gen`.
4. Изучите приложение.

## 3. Материалы для анализа

- **Словарь полей** (`iavd_incidents_raw3_field_dictionary.md/.docx`) —
  назначение каждого поля, типы, мультизначные JSON-поля и правила их
  разбора, производные поля скрипта (confusion, Flag_ValidLabel,
  Label_Status), предупреждения для расчётов.
- **Аннотированный скрипт** — инженерная логика ETL: слои каталогов,
  режимы отладки, справочники дат, матрица ошибок, порог классификации
  (по умолчанию 0.18 в приложении), шкала Харрингтона, палитра.
- Полезные контрольные точки: у 2 950 инференсов нет карточки; метрики
  качества считайте по `Flag_ValidLabel = 1`.
