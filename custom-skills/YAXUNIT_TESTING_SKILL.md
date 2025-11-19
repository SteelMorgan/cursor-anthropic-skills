---
name: yaxunit-testing
description: Skill for writing unit tests using YAxUnit framework for 1C:Enterprise (BSL). Use when creating, editing, or validating unit tests, working with test data generation, or implementing test assertions.
---

# YAxUnit Testing Framework Skill

## Introduction & When to Use

This skill provides mandatory procedures and best practices for writing unit tests using the YAxUnit framework for 1C:Enterprise (BSL) code.

**Trigger this skill when:**
- Creating or editing unit tests for 1C code
- Working in `tests/` directory (especially `tests/src/CommonModules`)
- Writing test assertions or test data generation code
- Setting up test module structure and registration
- Implementing test scenarios with YAxUnit API

**Keywords for detection:**
- `yaxunit`, `тест`, `тестирование`, `unit test`, `юнит тест`, `unit testing`
- `ЮТест`, `ЮТТесты`, `ИсполняемыеСценарии`
- Russian: `написать тест`, `создать тест`, `модульное тестирование`, `тест для 1С`

**Semantic triggers:**
- Creating/editing unit tests for 1C
- Writing test cases and scenarios
- Generating test data
- Implementing test assertions
- Setting up test infrastructure

---

## 🚨 CRITICAL: Absolute Compliance Requirements

**⚠️ THESE RULES ARE NON-NEGOTIABLE AND MUST BE FOLLOWED WITHOUT EXCEPTION ⚠️**

**Failure to follow these rules results in broken tests, incorrect test structure, or tests that won't run.**

### Core Test Creation Principles

**MANDATORY RULES - NO EXCEPTIONS ALLOWED:**

#### 1. 🚫 NEVER CREATE TESTS OUTSIDE STANDARD LOCATION

- **PROHIBITION**: Creating test modules anywhere except `tests/src/CommonModules`
- **MANDATORY LOCATION**: `tests/src/CommonModules/[ИмяМодуля]/`
- **CONSEQUENCE**: Tests won't be discovered by YAxUnit runner
- **ENFORCEMENT**: If path incorrect → STOP and use correct location

#### 2. 🚫 NEVER USE INCORRECT MODULE NAMING

- **PROHIBITION**: Module names without proper prefix/suffix
- **MANDATORY ACTION**: ALWAYS use `[Префикс]_[ИмяОбъекта][_Суффикс]` pattern
- **CONSEQUENCE**: Unclear what is being tested, violates conventions
- **ENFORCEMENT**: If naming incorrect → STOP and fix naming

#### 3. 🚫 NEVER OMIT ИСПОЛНЯЕМЫЕСЦЕНАРИИ PROCEDURE

- **PROHIBITION**: Test modules without `ИсполняемыеСценарии() Экспорт` procedure
- **MANDATORY ACTION**: ALWAYS include this procedure with test registration
- **CONSEQUENCE**: Tests won't be discovered and won't run
- **ENFORCEMENT**: If procedure missing → STOP and add it

#### 4. ✅ ALWAYS USE FLUENT INTERFACE

- **REQUIREMENT**: Use method chaining for test registration and assertions
- **MANDATORY PATTERN**: `ЮТТесты.ДобавитьТест().СПараметрами()...`
- **CONSEQUENCE**: Skip chaining = verbose, hard-to-read code
- **ENFORCEMENT**: Use fluent style for all YAxUnit API calls

#### 5. ✅ ALWAYS FOLLOW ARRANGE-ACT-ASSERT

- **REQUIREMENT**: Structure every test with clear AAA sections
- **MANDATORY SECTIONS**: Подготовка (Arrange) → Действие (Act) → Проверка (Assert)
- **CONSEQUENCE**: Skip structure = unclear test purpose and flow
- **ENFORCEMENT**: Mark sections with comments in code

#### 6. ✅ ALWAYS USE ФИКЦИЯ FOR TEST DATA

- **REQUIREMENT**: Prefer `.Фикция()` and `.ФикцияОбязательныхПолей()` over hardcoded values
- **MANDATORY ACTION**: Use generated data unless specific value required
- **CONSEQUENCE**: Hardcoded values = brittle tests, false positives
- **ENFORCEMENT**: Review data generation, replace hardcoded with `.Фикция()`

#### 7. ✅ ALWAYS DETECT PROJECT FORMAT (EDT vs DESIGNER)

- **REQUIREMENT**: Determine project format before creating metadata files
- **MANDATORY CHECK**: Look for `application-*.yml` or `yaxunit-*.yml` config file in workspace root
- **CRITICAL DECISION**: 
  - `format: DESIGNER` → Use `.xml` extension for metadata files
  - `format: EDT` → Use `.mdo` extension for metadata files
- **CONSEQUENCE**: Wrong extension = build failure, 1C won't recognize module
- **ENFORCEMENT**: If format unknown → **ASK USER** which format project uses

**Detection Protocol:**

```
Step 1: Search for config file
  - Look for files matching: application-*.yml, yaxunit-*.yml in workspace root
  - Read config file content
  - Find 'format:' field under 'app:' section

Step 2: Determine extension
  IF format: DESIGNER
    → metadata_extension = ".xml"
  ELSE IF format: EDT
    → metadata_extension = ".mdo"
  ELSE
    → ASK USER: "Does this project use EDT or Конфигуратор (DESIGNER)?"
    → Based on answer: EDT → .mdo, DESIGNER → .xml
```

**Example Config Detection:**

```yaml
# application-dssl-ut.yml
app:
  id: "project-name"
  format: DESIGNER    ← THIS DETERMINES FILE EXTENSION
  base-path: "..."
```

**File Naming Based on Format:**

| Format | Metadata File | Example |
|--------|---------------|---------|
| DESIGNER | `[ModuleName].xml` | `Док_ЛистПрайсЛиста_МО.xml` |
| EDT | `[ModuleName].mdo` | `Док_ЛистПрайсЛиста_МО.mdo` |

**CRITICAL ENFORCEMENT:**
- ❌ NEVER assume format without checking config
- ❌ NEVER create `.mdo` files in DESIGNER projects (won't build)
- ❌ NEVER create `.xml` files in EDT projects (won't build)
- ✅ ALWAYS check config file first
- ✅ ALWAYS ask user if config unclear or missing
- ✅ ALWAYS use correct extension for detected format

#### 8. ✅ ALWAYS CREATE METADATA FILE

- **REQUIREMENT**: Every test module needs metadata file (`.xml` or `.mdo` based on format)
- **MANDATORY ACTION**: Create `[ИмяМодуля].[extension]` with correct flags
- **CONSEQUENCE**: Module won't be recognized by 1C configuration
- **ENFORCEMENT**: If metadata file missing → STOP and create it

#### 9. ✅ ALWAYS REGISTER IN CONFIGURATION

- **REQUIREMENT**: Register test module in `tests/src/Configuration/Configuration.[xml|mdo]`
- **MANDATORY ACTION**: Add module entry to configuration metadata
- **CONSEQUENCE**: Module won't load in 1C, tests won't run
- **ENFORCEMENT**: Check registration after module creation

#### 10. ✅ ALWAYS BUILD AND RUN AFTER TEST CREATION

- **REQUIREMENT**: After creating test, build project and run test
- **MANDATORY SEQUENCE**: Create test → Build project → Run test
- **CONSEQUENCE**: Untested code may contain errors, test may not work
- **ENFORCEMENT**: If user asks to create test → must complete full cycle

#### 11. ✅ ALWAYS CHECK MCP LOGS ON ERRORS

- **REQUIREMENT**: When MCP operations fail, check logs for diagnostics
- **MANDATORY LOCATION**: `${workspaceFolder}/logs/yaxunit-mcp-log.log`
- **CONSEQUENCE**: Without logs, cannot diagnose MCP-related issues
- **ENFORCEMENT**: On MCP error → read log file → analyze error

#### 12. ✅ ALWAYS RUN SYNTAX CHECK AFTER BUILD

- **REQUIREMENT**: Run check_syntax_designer_modules after project build
- **MANDATORY ACTION**: Verify no syntax errors before running tests
- **CONSEQUENCE**: Skip check = potential runtime errors in tests
- **ENFORCEMENT**: If syntax errors found → fix and rebuild before running tests

### 🔴 CRITICAL ENFORCEMENT POLICY

- These rules are NOT suggestions or recommendations
- These rules are ABSOLUTE REQUIREMENTS
- Agent MUST NOT create tests without following structure
- Agent MUST NOT proceed if naming/location incorrect
- Agent MUST STOP and report if requirements cannot be met

**Violation examples that are STRICTLY FORBIDDEN:**

```
❌ "I'll create test in src/ instead of tests/src/CommonModules"
❌ "I'll skip metadata file, just create .bsl"
❌ "I'll use .mdo without checking if project uses DESIGNER"
❌ "I'll use hardcoded values instead of .Фикция()"
❌ "I'll skip ИсполняемыеСценарии, tests still work"
❌ "I don't need to register in Configuration"
❌ "I'll skip syntax check after build, tests will run anyway"
```

**Correct approach - MANDATORY statements:**

```
✅ "BEFORE creating test, I MUST check project format (EDT vs DESIGNER)"
✅ "BEFORE creating files, I MUST determine correct metadata extension (.xml or .mdo)"
✅ "BEFORE creating test, I MUST determine correct prefix and name"
✅ "BEFORE writing test code, I MUST create proper directory structure"
✅ "ALWAYS create both Module.bsl and metadata file with correct extension"
✅ "ALWAYS use .Фикция() for test data unless specific value needed"
✅ "AFTER creating module, I MUST register it in Configuration"
✅ "AFTER creating test, I MUST build project and run test"
✅ "AFTER build, I MUST run check_syntax_designer_modules() before running tests"
✅ "ON MCP error, I MUST check logs at ${workspaceFolder}/logs/yaxunit-mcp-log.log"
```

---

## Core Principles

### Test Module Location and Structure

**MANDATORY LOCATION:**
- All test modules: `tests/src/CommonModules/[ИмяМодуля]/`
- Test module file: `tests/src/CommonModules/[ИмяМодуля]/Module.bsl`
- Metadata file: `tests/src/CommonModules/[ИмяМодуля]/[ИмяМодуля].[xml|mdo]` (depends on format)
- Configuration: `tests/src/Configuration/Configuration.[xml|mdo]` (depends on format)

### Module Naming Convention

**Pattern:** `[Префикс]_[ИмяОбъекта][_Суффикс]`

#### Prefixes by Object Type

| Тип тестируемого объекта | Префикс | Пример |
|-------------------------|---------|--------|
| Общий модуль | `ОМ_` | ОМ_ОбщегоНазначения |
| Регистр бухгалтерии | `РБ_` | РБ_Хозрасчетный, РБ_Хозрасчетный_НЗ |
| Регистр накопления | `РН_` | РН_ОстаткиНаСкладах, РН_ОстаткиНаСкладах_ММ |
| Регистр расчета | `РР_` | РР_Зарплата, РР_Зарплата_НЗ |
| Регистр сведений | `РС_` | РС_АдресныйКлассификатор |
| Бизнес процесс | `БП_` | БП_Согласование |
| Справочник | `Спр_` | Спр_Пользователи, Спр_Пользователи_МО |
| План счетов | `ПС_` | ПС_Хозрасчетный |
| План видов расчета | `ПВР_` | ПВР_Зарплатный |
| План видов характеристик | `ПВХ_` | ПВХ_Субконто, ПВХ_Субконто_ММ |
| Документ | `Док_` | Док_ПКО |
| Перечисление | `Пер_` | Пер_СтатусСогласования |
| План обмена | `ПО_` | ПО_РИБ, ПО_РИБ_ММ |
| Задача | `Зад_` | Зад_Задача |
| Обработка | `Обр_` | Обр_ЗакрытиеМесяца, Обр_ЗакрытиеМесяца_МО |
| Отчет | `Отч_` | Отч_УниверсальныйОтчет |

#### Suffixes by Module Type

| Тип тестируемого модуля | Суффикс | Пример |
|------------------------|---------|--------|
| Общий модуль | `<Без суффикса>` | ОМ_ОбщегоНазначения |
| Модуль объекта | `_МО` | Спр_Пользователи_МО, Обр_ЗакрытиеМесяца_МО |
| Модуль менеджера | `_ММ` | ПВХ_Субконто_ММ, ПО_РИБ_ММ |
| Модуль набора записей | `_НЗ` | РБ_Хозрасчетный_НЗ, РР_Зарплата_НЗ |

**Examples:**
- Testing `Документ.ПоступлениеДенег` → Module name: `Док_ПоступлениеДенег`
- Testing `Справочник.Контрагенты` object module → Module name: `Спр_Контрагенты_МО`
- Testing `РегистрНакопления.ОстаткиТоваров` manager → Module name: `РН_ОстаткиТоваров_ММ`

### Test Module Structure

**MANDATORY STRUCTURE:**

```bsl
#Область СлужебныйПрограммныйИнтерфейс

// Регистрация тестов для выполнения
Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ИмяТеста")
            .СПараметрами(Параметр1, Параметр2, ОжидаемыйРезультат);
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура ИмяТеста(Параметр1, Параметр2, ОжидаемыйРезультат) Экспорт
    // Arrange (подготовка)
    
    // Act (действие)
    
    // Assert (проверка)
КонецПроцедуры

#КонецОбласти
```

### Arrange-Act-Assert Pattern

**MANDATORY TEST STRUCTURE:**

```bsl
Процедура ИмяТеста() Экспорт
    // Arrange (подготовка данных и начальных условий)
    // - Создание тестовых данных
    // - Настройка окружения
    // - Подготовка входных параметров
    
    // Act (выполнение тестируемого кода)
    // - Вызов тестируемой функции/процедуры
    // - Получение результата
    
    // Assert (проверка результатов)
    // - Проверка через ЮТест.ОжидаетЧто()
    // - Проверка базы данных через ЮТест.ОжидаетЧтоТаблицаБазы()
    // - Множественные проверки с fluent interface
КонецПроцедуры
```

---

## YAxUnit API Reference

### Module: ЮТТесты (Test Registration)

**Purpose:** Register tests to be executed by YAxUnit runner

**Usage in ИсполняемыеСценарии():**

```bsl
Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ИмяТеста")  // Register test by name
        .ДобавитьТест("ПараметризованныйТест")
            .СПараметрами(Значение1, Значение2, Ожидаемый1)  // Test with parameters
            .СПараметрами(Значение3, Значение4, Ожидаемый2); // Multiple parameter sets
КонецПроцедуры
```

**Methods:**
- `.ДобавитьТест(ИмяТеста: Строка)` - Register test procedure by name
- `.СПараметрами(Параметр1, Параметр2, ...)` - Add parameter set for parameterized test

**Key Rules:**
- Test name in `ДобавитьТест()` MUST match procedure name exactly
- Use fluent interface (method chaining)
- Each `.СПараметрами()` call creates separate test run

---

### Module: ЮТест.Данные() (Test Data Generation)

**Purpose:** Generate and manage test data (catalogs, documents, registers, etc.)

#### КонструкторОбъекта - Object Constructor

**Create and configure 1C objects with fluent interface:**

```bsl
Объект = ЮТест.Данные().КонструкторОбъекта("ТипОбъекта")
    .Установить("Реквизит", Значение)
    .ФикцияОбязательныхПолей()
    .Записать();
```

**Methods:**

##### Basic Configuration
- `.Установить(ИмяРеквизита: Строка, Значение: Произвольный)` - Set single attribute value
- `.УстановитьРеквизиты(ЗначенияРеквизитов: Структура)` - Set multiple attributes from structure

##### Фикция (Mock Data Generation)
- `.Фикция(ИмяРеквизита: Строка)` - Generate mock value for single attribute
- `.ФикцияРеквизитов(ИменаРеквизитов: Строка | Массив из Строка)` - Generate mock values for multiple attributes (comma-separated string or array)
- `.ФикцияОбязательныхПолей()` - Automatically generate mock values for all required fields

##### Tabular Sections
- `.ТабличнаяЧасть(ИмяТабличнойЧасти: Строка)` - Switch to tabular section context
- `.ДобавитьСтроку(ЗначенияРеквизитов: Структура = Неопределено)` - Add row to tabular section
- `.Объект()` - Return to object context (after working with tabular section)

##### Writing to Database
- `.Записать(ВернутьОбъект: Булево = Ложь, ОбменДаннымиЗагрузка: Булево = Ложь): Ссылка | Объект` - Write object to database
- `.Провести(ВернутьОбъект: Булево = Ложь): Ссылка | Объект` - Post document (write and post)
- `.ДобавитьЗапись(ОбменДаннымиЗагрузка: Булево)` - Write and return constructor (for chaining)
- `.НовыйОбъект()` - Create object without writing to database

##### Advanced
- `.УстановитьСсылкуНового(Значение: УникальныйИдентификатор | Строка)` - Set reference for new object
- `.УстановитьДополнительноеСвойство(ИмяСвойства: Строка, Значение: Произвольный)` - Set additional property
- `.ДанныеСтроки(): Структура | Неопределено` - Get current tabular section row data
- `.ДанныеОбъекта(): Структура` - Get object data as structure

**Example: Simple Catalog Creation**

```bsl
Контрагент = ЮТест.Данные().КонструкторОбъекта("Справочник.Контрагенты")
    .Установить("Наименование", "ООО Тестовый контрагент")
    .ФикцияОбязательныхПолей()  // Auto-fill required fields
    .Записать();
```

**Example: Document with Tabular Section**

```bsl
Документ = ЮТест.Данные().КонструкторОбъекта("Документ.ПриходТовара")
    .ФикцияОбязательныхПолей()
    .Установить("Контрагент", Поставщик)
    .ТабличнаяЧасть("Товары")
        .ДобавитьСтроку()
            .Установить("Номенклатура", Товар1)
            .Установить("Количество", 10)
            .Установить("Цена", 100)
        .ДобавитьСтроку()
            .Установить("Номенклатура", Товар2)
            .Установить("Количество", 5)
            .Установить("Цена", 200)
    .Провести(Истина);  // Post and return object
```

**CRITICAL: Prefer .Фикция() over hardcoded values**

```bsl
// ❌ BAD: Hardcoded values
Товар = ЮТест.Данные().КонструкторОбъекта("Справочник.Номенклатура")
    .Установить("Наименование", "Товар 1")
    .Установить("Артикул", "12345")
    .Установить("Поставщик", Справочники.Контрагенты.НайтиПоКоду("00001"))
    .Записать();

// ✅ GOOD: Use Фикция
Товар = ЮТест.Данные().КонструкторОбъекта("Справочник.Номенклатура")
    .ФикцияОбязательныхПолей()  // Generates all required data
    .Записать();

// ✅ GOOD: Mix specific values with Фикция
Товар = ЮТест.Данные().КонструкторОбъекта("Справочник.Номенклатура")
    .Установить("Наименование", "Специфичное наименование")  // Specific value needed for test
    .Фикция("Артикул")  // Generated value
    .Фикция("Поставщик")  // Generated value
    .Записать();
```

#### КонструкторДвижений - Document Movements Constructor

**Create register movements for documents:**

```bsl
ЮТест.Данные().КонструкторДвижений(Документ, "ИмяРегистра")
    .ДобавитьСтроку()
        .Установить("Измерение", Значение)
        .Установить("Ресурс", Значение)
    .Записать();
```

**Methods:**
- `.ДобавитьСтроку(ЗначенияРеквизитов: Структура = Неопределено)` - Add movement record
- `.Установить(ИмяРеквизита: Строка, Значение: Произвольный)` - Set dimension/resource value
- `.УстановитьРеквизиты(ЗначенияРеквизитов: Структура)` - Set multiple values
- `.Фикция(ИмяРеквизита: Строка, РеквизитыЗаполнения: Структура = Неопределено, ОграничениеТипа: Тип | ОписаниеТипов = Неопределено)` - Generate mock value
- `.ФикцияРеквизитов(ИменаРеквизитов: Строка | Массив из Строка)` - Generate mock values for multiple fields
- `.ФикцияОбязательныхПолей()` - Generate mock values for all required fields
- `.УстановитьДополнительноеСвойство(ИмяСвойства: Строка, Значение: Произвольный)` - Set additional property
- `.ДанныеСтроки(): Структура` - Get current row data
- `.Данные(): Массив` - Get all movement records
- `.Записать(ОбменДаннымиЗагрузка: Булево = Ложь)` - Write movements to database

**Example:**

```bsl
// Create empty document
Документ = ЮТест.Данные().СоздатьДокумент("Документ.ПриходнаяНакладная");

// Generate movements
ЮТест.Данные().КонструкторДвижений(Документ, "ОстаткиТоваров")
    .ДобавитьСтроку()
        .ФикцияРеквизитов("Номенклатура, Склад")  // Generate mock dimension values
        .Установить("Количество", 10)  // Specific resource value
    .ДобавитьСтроку()
        .ФикцияРеквизитов("Номенклатура, Склад")
        .Установить("Количество", 5)
    .Записать();
```

#### Other Data Generation Methods

- `ЮТест.Данные().СлучайнаяСтрока(Длина: Число = 10): Строка` - Generate random string
- `ЮТест.Данные().СоздатьДокумент(ТипДокумента: Строка)` - Create empty document without writing

**Example:**

```bsl
// Generate unique identifier for test
УникальныйАртикул = ЮТест.Данные().СлучайнаяСтрока(8);

// Use in assertions
ЮТест.ОжидаетЧто(Товар.Артикул).Равно(УникальныйАртикул);
```

---

### Module: ЮТест.ОжидаетЧто() (Assertions)

**Purpose:** Verify test results using fluent assertion interface

**Usage:**

```bsl
ЮТест.ОжидаетЧто(ФактическоеЗначение, "Описание проверки")
    .Равно(ОжидаемоеЗначение)
    .Свойство("ИмяСвойства").Заполнено()
    .Свойство("ДругоеСвойство").ИмеетТип("Тип");
```

**Key Features:**
- Fluent interface (method chaining)
- Optional description as second parameter
- Can chain multiple assertions
- Supports nested property checks

#### Comparison Assertions

- `.Равно(ОжидаемоеЗначение)` - Assert equals
- `.НеРавно(ОжидаемоеЗначение)` - Assert not equals
- `.Больше(ОжидаемоеЗначение)` - Assert greater than
- `.БольшеИлиРавно(ОжидаемоеЗначение)` - Assert greater than or equal
- `.Меньше(ОжидаемоеЗначение)` - Assert less than
- `.МеньшеИлиРавно(ОжидаемоеЗначение)` - Assert less than or equal

**Example:**

```bsl
ЮТест.ОжидаетЧто(Результат).Равно(42);
ЮТест.ОжидаетЧто(Сумма).Больше(0);
ЮТест.ОжидаетЧто(Количество).БольшеИлиРавно(1);
```

#### Type Assertions

- `.ЭтоНеопределено()` - Assert value is Undefined
- `.ЭтоНеНеопределено()` - Assert value is not Undefined
- `.ЭтоNull()` - Assert value is Null
- `.ЭтоНеNull()` - Assert value is not Null
- `.ЭтоИстина()` - Assert value is True
- `.ЭтоНеИстина()` - Assert value is not True
- `.ЭтоЛожь()` - Assert value is False
- `.ЭтоНеЛожь()` - Assert value is not False
- `.ИмеетТип(Тип)` - Assert value has specific type
- `.НеИмеетТип(Тип)` - Assert value doesn't have specific type

**Example:**

```bsl
ЮТест.ОжидаетЧто(Ссылка).ЭтоНеНеопределено();
ЮТест.ОжидаетЧто(Документ.Проведен).ЭтоИстина();
ЮТест.ОжидаетЧто(Товар).ИмеетТип("СправочникСсылка.Номенклатура");
```

#### Filled/Empty Assertions

- `.Заполнено()` - Assert value is filled (not empty, not zero, not Undefined)
- `.НеЗаполнено()` - Assert value is not filled
- `.Существует()` - Assert object/reference exists in database
- `.НеСуществует()` - Assert object/reference doesn't exist in database

**Example:**

```bsl
ЮТест.ОжидаетЧто(Контрагент.Наименование).Заполнено();
ЮТест.ОжидаетЧто(Ссылка).Существует();
```

#### Collection Assertions

- `.ИмеетДлину(Длина)` - Assert collection/string has specific length
- `.ИмеетДлинуБольше(Длина)` - Assert collection/string length is greater
- `.ИмеетДлинуМеньше(Длина)` - Assert collection/string length is less
- `.НеИмеетДлину(Длина)` - Assert collection/string doesn't have specific length
- `.Содержит(Значение)` - Assert collection contains value
- `.НеСодержит(Значение)` - Assert collection doesn't contain value
- `.ВСписке(Массив)` - Assert value is in array

**Example:**

```bsl
ЮТест.ОжидаетЧто(Документ.Товары).ИмеетДлину(5);
ЮТест.ОжидаетЧто(СписокТоваров).Содержит(Товар);
ЮТест.ОжидаетЧто(Статус).ВСписке(ДопустимыеСтатусы);
```

#### String Assertions

- `.НачинаетсяС(ПрефиксСтроки)` - Assert string starts with prefix
- `.ЗаканчиваетсяНа(СуффиксСтроки)` - Assert string ends with suffix
- `.СодержитСтрокуПоШаблону(Шаблон)` - Assert string matches pattern (regex)
- `.НеСодержитСтрокуПоШаблону(Шаблон)` - Assert string doesn't match pattern

**Example:**

```bsl
ЮТест.ОжидаетЧто(Артикул).НачинаетсяС("АРТ-");
ЮТест.ОжидаетЧто(ИмяФайла).ЗаканчиваетсяНа(".xml");
```

#### Range Assertions

- `.МеждуВключаяГраницы(Минимум, Максимум)` - Assert value is between min and max (inclusive)
- `.МеждуИсключаяГраницы(Минимум, Максимум)` - Assert value is between min and max (exclusive)
- `.МеждуВключаяНачалоГраницы(Минимум, Максимум)` - Assert value >= min and < max
- `.МеждуВключаяОкончаниеГраницы(Минимум, Максимум)` - Assert value > min and <= max

**Example:**

```bsl
ЮТест.ОжидаетЧто(Цена).МеждуВключаяГраницы(100, 1000);
ЮТест.ОжидаетЧто(Процент).МеждуВключаяГраницы(0, 100);
```

#### Property Assertions

- `.Свойство(ИмяСвойства)` - Access object property for chained assertion
- `.ИмеетСвойство(ИмяСвойства)` - Assert object has property
- `.НеИмеетСвойства(ИмяСвойства)` - Assert object doesn't have property
- `.ИмеетСвойстваРавные(Структура)` - Assert multiple properties match values in structure

**Example:**

```bsl
// Chain property checks
ЮТест.ОжидаетЧто(Документ)
    .Свойство("Номер").Заполнено()
    .Свойство("Дата").Заполнено()
    .Свойство("Контрагент").ИмеетТип("СправочникСсылка.Контрагенты")
    .Свойство("Сумма").Больше(0);

// Check property existence
ЮТест.ОжидаетЧто(Структура).ИмеетСвойство("Ключ");

// Check multiple properties at once
ОжидаемыеЗначения = Новый Структура("Проведен, ПометкаУдаления", Истина, Ложь);
ЮТест.ОжидаетЧто(Документ).ИмеетСвойстваРавные(ОжидаемыеЗначения);
```

**Array/Tabular Section Element Access:**

```bsl
// Access by index
ЮТест.ОжидаетЧто(Документ)
    .Свойство("Товары[0].Номенклатура").Равно(Товар1)
    .Свойство("Товары[0].Количество").Равно(10);

// Access last element with negative index
ЮТест.ОжидаетЧто(Документ)
    .Свойство("Товары[-1].Номенклатура").Равно(ПоследнийТовар);
```

#### Collection Element Assertions

- `.КаждыйЭлементСодержитСвойство(ИмяСвойства)` - Assert all elements have property
- `.КаждыйЭлементСодержитСвойствоСоЗначением(ИмяСвойства, Значение)` - Assert all elements have property with value
- `.ЛюбойЭлементСодержитСвойство(ИмяСвойства)` - Assert at least one element has property
- `.ЛюбойЭлементСодержитСвойствоСоЗначением(ИмяСвойства, Значение)` - Assert at least one element has property with value
- `.КаждыйЭлементСоответствуетПредикату(Предикат)` - Assert all elements match predicate
- `.ЛюбойЭлементСоответствуетПредикату(Предикат)` - Assert at least one element matches predicate

**Example:**

```bsl
// All rows must have filled Nomenclature
ЮТест.ОжидаетЧто(Документ.Товары).КаждыйЭлементСодержитСвойство("Номенклатура");

// At least one row with specific value
ЮТест.ОжидаетЧто(Документ.Товары).ЛюбойЭлементСодержитСвойствоСоЗначением("Номенклатура", Товар1);
```

#### Complete Example with Fluent Interface

```bsl
// Complex assertion with multiple chained checks
ЮТест.ОжидаетЧто(Документ, "Проверка созданного документа")
    .Заполнено()
    .ИмеетТип("ДокументСсылка.ПриходТовара")
    .Существует()
    .Свойство("Номер").Заполнено()
    .Свойство("Дата").Заполнено()
    .Свойство("Контрагент").Равно(Поставщик)
    .Свойство("Склад").Равно(Склад)
    .Свойство("Товары").ИмеетДлину(2)
    .Свойство("Товары[0].Номенклатура").Равно(Товар1)
    .Свойство("Товары[0].Количество").Равно(10)
    .Свойство("Товары[0].Цена").Больше(0)
    .Свойство("Товары[-1].Номенклатура").Равно(Товар2)
    .Свойство("Проведен").ЭтоИстина();
```

---

### Module: ЮТест.ОжидаетЧтоТаблицаБазы() (Database Assertions)

**Purpose:** Verify data in database tables (catalogs, documents, registers)

**Usage:**

```bsl
ЮТест.ОжидаетЧтоТаблицаБазы("ИмяТаблицы", "Описание проверки")
    .СодержитЗаписи(Предикат);
```

**Methods:**

#### Record Existence
- `.СодержитЗаписи(Предикат = Неопределено)` - Assert table contains records (optionally matching predicate)
- `.НеСодержитЗаписи(Предикат = Неопределено)` - Assert table doesn't contain records (optionally matching predicate)

#### Specific Field Checks
- `.СодержитЗаписиСНаименованием(Наименование)` - Assert table contains records with specific Наименование
- `.СодержитЗаписиСКодом(Код)` - Assert table contains records with specific Код
- `.СодержитЗаписиСНомером(Номер)` - Assert table contains records with specific Номер (for documents)
- `.НеСодержитЗаписиСНаименованием(Наименование)` - Assert table doesn't contain records with specific Наименование
- `.НеСодержитЗаписиСКодом(Код)` - Assert table doesn't contain records with specific Код
- `.НеСодержитЗаписиСНомером(Номер)` - Assert table doesn't contain records with specific Номер

**Table Names:**
- Catalogs: `"Справочник.ИмяСправочника"`
- Documents: `"Документ.ИмяДокумента"`
- Registers: `"РегистрСведений.ИмяРегистра"`, `"РегистрНакопления.ИмяРегистра"`, etc.

**Example: Simple Check**

```bsl
// Check catalog contains records
ЮТест.ОжидаетЧтоТаблицаБазы("Справочник.Контрагенты")
    .СодержитЗаписи();

// Check catalog contains record with specific name
ЮТест.ОжидаетЧтоТаблицаБазы("Справочник.Контрагенты")
    .СодержитЗаписиСНаименованием("ООО Тестовый");
```

**Example: With Predicate**

```bsl
// Verify record doesn't exist before test
АртикулТовара = ЮТест.Данные().СлучайнаяСтрока();
Предикат = ЮТест.Предикат()
    .Реквизит("Артикул").Равно(АртикулТовара)
    .Получить();

ЮТест.ОжидаетЧтоТаблицаБазы("Справочник.Товары", "Товар с таким артикулом не существует")
    .НеСодержитЗаписей(Предикат);

// Create record
Товар = ЮТест.Данные().КонструкторОбъекта("Справочник.Товары")
    .Установить("Артикул", АртикулТовара)
    .ФикцияОбязательныхПолей()
    .Записать();

// Verify record exists after creation
ЮТест.ОжидаетЧтоТаблицаБазы("Справочник.Товары", "Товар создан в базе")
    .СодержитЗаписей(Предикат);
```

---

### Module: ЮТест.Предикат() (Predicate Builder)

**Purpose:** Build complex conditions for database assertions

**Usage:**

```bsl
Предикат = ЮТест.Предикат()
    .Реквизит("ИмяРеквизита").Равно(Значение)
    .Реквизит("ДругойРеквизит").НеРавно(Значение)
    .Получить();  // IMPORTANT: Call .Получить() to get predicate object
```

**Methods:**
- `.Реквизит(ИмяРеквизита).Равно(Значение)` - Add equals condition
- `.Реквизит(ИмяРеквизита).НеРавно(Значение)` - Add not equals condition
- `.Получить()` - **CRITICAL:** Return built predicate (must call at end!)

**Example:**

```bsl
// Build predicate for complex condition
Предикат = ЮТест.Предикат()
    .Реквизит("Контрагент").Равно(ТестовыйКонтрагент)
    .Реквизит("Сумма").Больше(1000)
    .Получить();  // Must call to get predicate object!

// Use in database assertion
ЮТест.ОжидаетЧтоТаблицаБазы("Документ.Счет")
    .СодержитЗаписей(Предикат);
```

**CRITICAL:** Always call `.Получить()` at the end of predicate chain to return the predicate object for use in assertions.

---

### Module: ЮТест.Контекст() (Test Context)

**Purpose:** Store and retrieve data between tests or test stages

**Usage:**

```bsl
// Store value
ЮТест.Контекст().УстановитьЗначение("КлючДанных", Значение);

// Retrieve value
ЗначениеИзКонтекста = ЮТест.Контекст().Значение("КлючДанных");
```

**Methods:**
- `.Значение(ИмяЗначения: Строка): Произвольный` - Get value from context
- `.УстановитьЗначение(ИмяЗначения: Строка, Значение: Произвольный)` - Set value in context

**Use Cases:**
- Share data between test setup and test execution
- Store data created in `ПередВсемиТестами()` for use in tests
- Pass data between related tests

**Example:**

```bsl
// In ПередВсемиТестами - create shared test data
Процедура ПередВсемиТестами() Экспорт
    ТестовыйКонтрагент = ЮТест.Данные().КонструкторОбъекта("Справочник.Контрагенты")
        .ФикцияОбязательныхПолей()
        .Записать();
    
    ЮТест.Контекст().УстановитьЗначение("ТестовыйКонтрагент", ТестовыйКонтрагент);
КонецПроцедуры

// In test - use shared data
Процедура СозданиеДокумента() Экспорт
    // Arrange
    Контрагент = ЮТест.Контекст().Значение("ТестовыйКонтрагент");
    
    // Act
    Документ = ЮТест.Данные().КонструкторОбъекта("Документ.Счет")
        .Установить("Контрагент", Контрагент)
        .ФикцияОбязательныхПолей()
        .Записать();
    
    // Assert
    ЮТест.ОжидаетЧто(Документ.Контрагент).Равно(Контрагент);
КонецПроцедуры
```

---

## Event Handlers (Optional)

**Purpose:** Setup and teardown logic that runs at specific points in test execution

**Available Handlers:**

```bsl
// Runs once before all tests in module
Процедура ПередВсемиТестами() Экспорт
    // Setup shared test data
    // Initialize test environment
КонецПроцедуры

// Runs once before each test набор (group of tests)
Процедура ПередТестовымНабором() Экспорт
    // Setup for test набор
КонецПроцедуры

// Runs before EACH test
Процедура ПередКаждымТестом() Экспорт
    // Clean state before each test
    // Setup test-specific data
КонецПроцедуры

// Runs after EACH test
Процедура ПослеКаждогоТеста() Экспорт
    // Cleanup after each test
    // Delete test data
КонецПроцедуры

// Runs once after each test набор
Процедура ПослеТестовогоНабора() Экспорт
    // Cleanup after test набор
КонецПроцедуры

// Runs once after all tests in module
Процедура ПослеВсехТестов() Экспорт
    // Final cleanup
    // Remove shared test data
КонецПроцедуры
```

**Key Rules:**
- All handlers are OPTIONAL
- Handlers must be `Экспорт` procedures
- Handlers take NO parameters
- Use `ЮТест.Контекст()` to share data between handlers and tests

**Common Patterns:**

```bsl
// Pattern: Shared test data
Процедура ПередВсемиТестами() Экспорт
    ТестовыйКонтрагент = ЮТест.Данные().КонструкторОбъекта("Справочник.Контрагенты")
        .ФикцияОбязательныхПолей()
        .Записать();
    
    ЮТест.Контекст().УстановитьЗначение("Контрагент", ТестовыйКонтрагент);
КонецПроцедуры

Процедура ПослеВсехТестов() Экспорт
    Контрагент = ЮТест.Контекст().Значение("Контрагент");
    Если ЗначениеЗаполнено(Контрагент) Тогда
        Контрагент.ПолучитьОбъект().Удалить();
    КонецЕсли;
КонецПроцедуры
```

---

## Mandatory File Structure

### Directory Structure

**CRITICAL: Directory structure is DIFFERENT for DESIGNER vs EDT formats!**

#### DESIGNER Format (File-based 1C databases)

```
tests/
└── src/
    ├── CommonModules/
    │   ├── [ИмяМодуля].xml                  ← Metadata file in ROOT of CommonModules/
    │   └── [ИмяМодуля]/                     ← Module directory
    │       └── Ext/                         ← Ext subdirectory (MANDATORY!)
    │           └── Module.bsl               ← Test code inside Ext/
    └── Configuration/
        └── Configuration.xml                ← Registration file
```

**Example (DESIGNER):**
```
tests/src/CommonModules/
├── Док_ЛистПрайсЛиста_МО.xml               ← Metadata in root
└── Док_ЛистПрайсЛиста_МО/                  ← Module folder
    └── Ext/                                 ← Ext subfolder
        └── Module.bsl                       ← Code in Ext/
```

#### EDT Format (Enterprise Development Tools)

```
tests/
└── src/
    ├── CommonModules/
    │   └── [ИмяМодуля]/                     ← Module directory
    │       ├── [ИмяМодуля].mdo              ← Metadata file INSIDE module directory
    │       └── Module.bsl                   ← Test code DIRECTLY in module directory
    └── Configuration/
        └── Configuration.mdo                ← Registration file
```

**Example (EDT):**
```
tests/src/CommonModules/
└── Док_ЛистПрайсЛиста_МО/                  ← Module folder
    ├── Док_ЛистПрайсЛиста_МО.mdo           ← Metadata inside
    └── Module.bsl                           ← Code directly here
```

#### Key Differences Summary

| Aspect | DESIGNER | EDT |
|--------|----------|-----|
| Metadata location | `CommonModules/[Name].xml` (root) | `CommonModules/[Name]/[Name].mdo` (inside) |
| Code location | `CommonModules/[Name]/Ext/Module.bsl` | `CommonModules/[Name]/Module.bsl` |
| Ext/ subfolder | **REQUIRED** | **NOT USED** |
| Extension | `.xml` | `.mdo` |

**CRITICAL ENFORCEMENT:**
- ❌ NEVER mix structures (Ext/ folder in EDT, or no Ext/ in DESIGNER)
- ❌ NEVER put metadata inside module folder for DESIGNER
- ❌ NEVER put metadata in root for EDT
- ✅ ALWAYS detect format first via `application-*.yml`
- ✅ ALWAYS use correct structure for detected format
- ✅ ALWAYS verify structure matches working modules (check `exts/yaxunit/CommonModules/`)

### Module.bsl Template

```bsl
#Область СлужебныйПрограммныйИнтерфейс

Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ИмяТеста");
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура ИмяТеста() Экспорт
    // Arrange
    
    // Act
    
    // Assert
КонецПроцедуры

#КонецОбласти
```

### Metadata File Templates

**CRITICAL: Templates are DIFFERENT for DESIGNER vs EDT formats!**

#### DESIGNER Format (`.xml` file in CommonModules root)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<MetaDataObject xmlns="http://v8.1c.ru/8.3/MDClasses" xmlns:app="http://v8.1c.ru/8.2/managed-application/core" xmlns:cfg="http://v8.1c.ru/8.1/data/enterprise/current-config" xmlns:cmi="http://v8.1c.ru/8.2/managed-application/cmi" xmlns:ent="http://v8.1c.ru/8.1/data/enterprise" xmlns:lf="http://v8.1c.ru/8.2/managed-application/logform" xmlns:style="http://v8.1c.ru/8.1/data/ui/style" xmlns:sys="http://v8.1c.ru/8.1/data/ui/fonts/system" xmlns:v8="http://v8.1c.ru/8.1/data/core" xmlns:v8ui="http://v8.1c.ru/8.1/data/ui" xmlns:web="http://v8.1c.ru/8.1/data/ui/colors/web" xmlns:win="http://v8.1c.ru/8.1/data/ui/colors/windows" xmlns:xen="http://v8.1c.ru/8.3/xcf/enums" xmlns:xpr="http://v8.1c.ru/8.3/xcf/predef" xmlns:xr="http://v8.1c.ru/8.3/xcf/readable" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="2.20">
	<CommonModule uuid="GENERATED_UUID">
		<Properties>
			<Name>[ИмяМодуля]</Name>
			<Synonym>
				<v8:item>
					<v8:lang>ru</v8:lang>
					<v8:content>[Описание модуля]</v8:content>
				</v8:item>
			</Synonym>
			<Comment/>
			<Global>false</Global>
			<ClientManagedApplication>false</ClientManagedApplication>
			<Server>true</Server>
			<ExternalConnection>false</ExternalConnection>
			<ClientOrdinaryApplication>false</ClientOrdinaryApplication>
			<ServerCall>false</ServerCall>
			<Privileged>false</Privileged>
			<ReturnValuesReuse>DontUse</ReturnValuesReuse>
		</Properties>
	</CommonModule>
</MetaDataObject>
```

**DESIGNER specifics:**
- File location: `tests/src/CommonModules/[ИмяМодуля].xml` (root of CommonModules/)
- Schema: `<MetaDataObject>` root element
- More verbose XML with namespaces
- Used in file-based 1C databases (DESIGNER format)

#### EDT Format (`.mdo` file inside module directory)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<mdclass:CommonModule xmlns:mdclass="http://g5.1c.ru/v8/dt/metadata/mdclass" uuid="GENERATED_UUID">
  <name>[ИмяМодуля]</name>
  <clientManagedApplication>false</clientManagedApplication>
  <server>true</server>
  <clientOrdinaryApplication>false</clientOrdinaryApplication>
</mdclass:CommonModule>
```

**EDT specifics:**
- File location: `tests/src/CommonModules/[ИмяМодуля]/[ИмяМодуля].mdo` (inside module dir)
- Schema: `<mdclass:CommonModule>` root element
- Simpler, more compact XML
- Used in EDT (Enterprise Development Tools) projects

#### Flag Settings (same for both formats)

**CRITICAL: For tests to access configuration objects (`Документы`, `Справочники`, etc.), module MUST be server-only!**

| Module Type | server | clientManagedApplication | clientOrdinaryApplication | Notes |
|-------------|--------|--------------------------|---------------------------|-------|
| **General test module (RECOMMENDED)** | **true** | **false** | **false** | **Server-only: required for access to `Документы.*`, `Справочники.*`, etc.** |
| Object/Manager test (_МО, _ММ) | true | false | false | Server-only |
| Client test (UI tests) | false | true | true | Client-only, NO access to server objects |

**CRITICAL ENFORCEMENT:**

❌ **NEVER** set `clientManagedApplication=true` or `clientOrdinaryApplication=true` for tests that:
- Access `Документы.*` objects
- Access `Справочники.*` objects  
- Access `РегистрыСведений.*`, `РегистрыНакопления.*`, etc.
- Use `ЮТест.Данные().КонструкторОбъекта()` to create database objects
- Test server-side business logic

✅ **ALWAYS** use **server-only** flags (`server=true`, others `false`) for:
- Testing documents, catalogs, registers
- Testing object modules (_МО)
- Testing manager modules (_ММ)
- Testing recordset modules (_НЗ)
- ANY test that creates/reads/writes database objects

**Why this matters:**
- Client-side code CANNOT access `Документы`, `Справочники` directly
- Error: `Переменная не определена (Документы)` = module runs on client, not server
- YAxUnit tests with database operations MUST run on server
- Only UI/form tests should use client flags

**Common error pattern:**
```
Error: {TESTS ОбщийМодуль.Test_МО.Модуль(30,13)}: Переменная не определена (Документы)
Cause: clientManagedApplication=true or clientOrdinaryApplication=true
Fix: Set both to false, keep only server=true
```

**Match flags to the module being tested!**

**NOTE:** Both templates above (DESIGNER and EDT) use **server-only** flags (`server=true`, client flags `false`) as this is the REQUIRED configuration for 99% of YAxUnit tests. Only change flags if you specifically need client-side testing (UI tests).

#### Critical Rules

- **NEVER** mix templates (EDT template for DESIGNER or vice versa)
- **NEVER** update existing metadata file if it already exists
- **ALWAYS** generate new UUID for new modules (use UUID v4 format)
- **ALWAYS** use correct template based on project format
- **ALWAYS** set flags to match the module being tested
- **ALWAYS** verify file location matches format (root vs inside directory)

### Configuration Registration

After creating test module, **MUST** register in `tests/src/Configuration/Configuration.[xml|mdo]`:

```xml
<commonModules>
  <!-- Existing modules -->
  <commonModule>[ИмяМодуля]</commonModule>
</commonModules>
```

**Note:** File extension (`.xml` or `.mdo`) depends on project format.

---

## Mandatory Workflows

### Workflow 1: Creating New Test Module

**COMPLETE SEQUENCE - NO EXCEPTIONS:**

```
Step 0: Detect Project Format (MANDATORY FIRST STEP)
├─ Search for: application-*.yml or yaxunit-*.yml
├─ Read config file → find 'format:' field
├─ IF format: DESIGNER → store: format="DESIGNER", ext=".xml"
├─ IF format: EDT → store: format="EDT", ext=".mdo"
├─ IF config not found or unclear → ASK USER
└─ Store: format variable and metadata_extension variable

Step 1: Determine Naming
├─ Identify object type → determine prefix (ОМ_, Док_, Спр_, etc.)
├─ Identify module type → determine suffix (_МО, _ММ, _НЗ, or none)
└─ Form name: [Префикс]_[ИмяОбъекта][_Суффикс]

Step 2: Create Directory Structure (FORMAT-DEPENDENT!)
├─ IF DESIGNER format:
│   ├─ Create: tests/src/CommonModules/[ИмяМодуля]/
│   ├─ Create: tests/src/CommonModules/[ИмяМодуля]/Ext/
│   └─ Verify: Ext/ subdirectory exists
├─ IF EDT format:
│   ├─ Create: tests/src/CommonModules/[ИмяМодуля]/
│   └─ Verify: NO Ext/ subdirectory
└─ Verify path is correct

Step 3: Create Metadata File (FORMAT-DEPENDENT!)
├─ Generate new UUID
├─ Set correct flags (match tested module)
├─ Use extension from Step 0 (metadata_extension)
├─ IF DESIGNER format:
│   ├─ Write: tests/src/CommonModules/[ИмяМодуля].xml (ROOT of CommonModules/)
│   └─ Format: DESIGNER XML (MetaDataObject schema)
├─ IF EDT format:
│   ├─ Write: tests/src/CommonModules/[ИмяМодуля]/[ИмяМодуля].mdo (INSIDE module dir)
│   └─ Format: EDT MDO (mdclass schema)
└─ IF file exists → SKIP, don't overwrite

Step 4: Create Module.bsl (FORMAT-DEPENDENT!)
├─ Use template structure
├─ Add ИсполняемыеСценарии() procedure
├─ Add region markers
├─ IF DESIGNER format:
│   └─ Write: tests/src/CommonModules/[ИмяМодуля]/Ext/Module.bsl (INSIDE Ext/)
├─ IF EDT format:
│   └─ Write: tests/src/CommonModules/[ИмяМодуля]/Module.bsl (DIRECT in module dir)
└─ Verify file written to correct location

Step 5: Register in Configuration (FORMAT-DEPENDENT!)
├─ Read: tests/src/Configuration/Configuration.[xml|mdo] (depends on format)
├─ Add entry to <commonModules> section
└─ Write updated Configuration file

Step 6: Verify Structure
├─ Check all files created
├─ Check naming follows convention
├─ Check correct file extensions used
├─ Check registration complete
├─ IF DESIGNER: verify Ext/ folder exists and Module.bsl inside it
├─ IF DESIGNER: verify metadata file in CommonModules root
├─ IF EDT: verify NO Ext/ folder
└─ IF EDT: verify metadata file inside module directory
```

**ENFORCEMENT:** 
- ALL steps MANDATORY
- Cannot skip Step 0 (format detection)
- MUST use correct directory structure for detected format
- If any step fails → STOP and report error
- If unsure about format → ASK USER before proceeding

---

### Workflow 2: Build and Run Test After Creation

**COMPLETE SEQUENCE - NO EXCEPTIONS:**

```
Step 1: Verify Test Module Created
├─ Check Module.bsl exists
├─ Check .mdo exists
├─ Check registration in Configuration.mdo
└─ Verify ИсполняемыеСценарии() present

Step 2: Build Project
├─ Execute build command (via terminal or build tool)
├─ Wait for build completion
├─ Check for build errors
└─ IF build fails → Check logs and fix errors

Step 2.5: Designer Modules Syntax Check
├─ Execute: check_syntax_designer_modules()
├─ Check for syntax errors in test modules
├─ Review ERROR/WARNING levels in results
├─ IF ERROR found:
│  ├─ Fix errors in test modules
│  ├─ Rebuild project
│  └─ Repeat Step 2.5
├─ IF only WARNING found:
│  └─ Assess criticality, fix if needed
└─ IF no errors → Proceed to Step 3

Step 3: Run Test
├─ Execute test run command
├─ Wait for test completion
├─ Check test results
└─ IF test fails → Analyze failure and fix

Step 4: Handle Errors
├─ IF MCP operation fails → Read ${workspaceFolder}/logs/yaxunit-mcp-log.log
├─ IF build fails → Check build output
├─ IF test fails → Check test output and assertions
└─ Report errors to user with diagnostic information
```

**ENFORCEMENT:** When user asks to create test → MUST complete Steps 1-3. Cannot deliver test without building and running.

**MCP Log Location:** `${workspaceFolder}/logs/yaxunit-mcp-log.log`

---

### Workflow 3: Writing Single Test

**COMPLETE SEQUENCE - NO EXCEPTIONS:**

```
Step 1: Plan Test
├─ Identify what to test (function/procedure/scenario)
├─ Determine test name (descriptive, matches procedure)
└─ Identify test data requirements

Step 2: Register Test
├─ Add to ИсполняемыеСценарии()
├─ Use: ЮТТесты.ДобавитьТест("ИмяТеста")
└─ Use fluent interface

Step 3: Create Test Procedure
├─ Add in #Область Тесты
├─ Signature: Процедура ИмяТеста() Экспорт
├─ Name MUST match registration exactly
└─ Add Arrange-Act-Assert structure

Step 4: Implement Arrange
├─ Use ЮТест.Данные().КонструкторОбъекта()
├─ Prefer .Фикция() over hardcoded values
├─ Create minimal test data required
└─ Store in variables

Step 5: Implement Act
├─ Call tested function/procedure
├─ Pass test data from Arrange
└─ Store result

Step 6: Implement Assert
├─ Use ЮТест.ОжидаетЧто()
├─ Use fluent interface for multiple checks
├─ Add descriptive messages
└─ Check all relevant aspects of result
```

**ENFORCEMENT:** Follow AAA structure. Use .Фикция(). Use fluent interface.

---

### Workflow 4: Parameterized Test

**COMPLETE SEQUENCE - NO EXCEPTIONS:**

```
Step 1: Register with Parameters
Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ИмяТеста")
            .СПараметрами(Значение1, Значение2, Ожидаемый1)
            .СПараметрами(Значение3, Значение4, Ожидаемый2)
            .СПараметрами(Значение5, Значение6, Ожидаемый3);
КонецПроцедуры

Step 2: Define Test with Parameters
Процедура ИмяТеста(Параметр1, Параметр2, ОжидаемыйРезультат) Экспорт
    // Parameters come from .СПараметрами()
    
    // Arrange
    // Use parameters
    
    // Act
    Результат = ТестируемаяФункция(Параметр1, Параметр2);
    
    // Assert
    ЮТест.ОжидаетЧто(Результат).Равно(ОжидаемыйРезультат);
КонецПроцедуры
```

**Key Rules:**
- Parameter count in procedure MUST match count in each `.СПараметрами()`
- Parameter order MUST match
- Each `.СПараметрами()` creates separate test run
- Use parameterized tests for: different inputs, boundary values, equivalence classes

---

### Workflow 5: Test Data Cleanup

**Best Practice Pattern:**

```bsl
#Область Тесты

Процедура ТестСозданияОбъекта() Экспорт
    // Arrange
    СозданныеОбъекты = Новый Массив;
    
    Попытка
        Объект1 = ЮТест.Данные().КонструкторОбъекта("Справочник.Контрагенты")
            .ФикцияОбязательныхПолей()
            .Записать();
        СозданныеОбъекты.Добавить(Объект1);
        
        // Act
        // ... test logic ...
        
        // Assert
        // ... assertions ...
        
    Исключение
        // Cleanup even if test fails
        Для Каждого Объект Из СозданныеОбъекты Цикл
            Попытка
                Объект.ПолучитьОбъект().Удалить();
            Исключение
            КонецПопытки;
        КонецЦикла;
        
        ВызватьИсключение;
    КонецПопытки;
    
    // Normal cleanup after successful test
    Для Каждого Объект Из СозданныеОбъекты Цикл
        Объект.ПолучитьОбъект().Удалить();
    КонецЦикла;
КонецПроцедуры

#КонецОбласти
```

**Alternative: Use Event Handlers**

```bsl
Процедура ПослеКаждогоТеста() Экспорт
    // Get objects from context and cleanup
    СозданныеОбъекты = ЮТест.Контекст().Значение("СозданныеОбъекты");
    Если СозданныеОбъекты <> Неопределено Тогда
        Для Каждого Объект Из СозданныеОбъекты Цикл
            Попытка
                Объект.ПолучитьОбъект().Удалить();
            Исключение
            КонецПопытки;
        КонецЦикла;
    КонецЕсли;
КонецПроцедуры
```

---

## Integration with BSL Rules

This skill works together with other BSL development rules:

### Integration with 1C_BSL_SKILL.md

When creating test data for real configuration objects:

```
1. Use 1C_BSL_SKILL validation for metadata
   └─ Call search_metadata() to verify object exists
   └─ Call search_metadata(op: "object_structure") to verify attributes

2. Use 1C_BSL_SKILL validation for API
   └─ If calling platform API in tests → validate with getMembers()
   └─ If using specific methods → validate with getMember()

3. Follow anti-hallucination rules
   └─ NEVER assume object/attribute exists
   └─ ALWAYS validate through MCP tools before using in test
```

**Example Integration:**

```
User: "Create test for Справочник.Контрагенты write"

Agent workflow:
1. Load YAXUNIT_TESTING_SKILL (detected keyword "test")
2. Load 1C_BSL_SKILL (working with 1C metadata)
3. Validate metadata: search_metadata("Контрагенты")
4. Get structure: search_metadata(op: "object_structure", object: "Контрагенты")
5. Create test using validated attributes
6. Use .Фикция() for non-critical attributes
```

### Integration with project_bsl_rules.mdc

When creating test files:

```
1. IF project_bsl_rules.mdc requires comment blocks:
   └─ Follow commenting rules for test file changes
   └─ Add //++ blocks for new test procedures
   └─ Get Moscow time via MCP before commenting

2. IF project has registry requirements:
   └─ Update registry.md with test module info

3. Follow all project-specific rules
   └─ UTF-8 encoding for Russian text
   └─ Code style requirements
   └─ Naming conventions
```

**Key Point:** YAxUnit testing rules take precedence for TEST structure, but project rules apply for HOW tests are created and documented.

---

## Examples

### Example 1: Simple Catalog Test

```bsl
#Область СлужебныйПрограммныйИнтерфейс

Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("СозданиеКонтрагента");
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура СозданиеКонтрагента() Экспорт
    // Arrange (подготовка)
    Наименование = ЮТест.Данные().СлучайнаяСтрока();
    
    // Act (действие)
    Контрагент = ЮТест.Данные().КонструкторОбъекта("Справочник.Контрагенты")
        .Установить("Наименование", Наименование)
        .ФикцияОбязательныхПолей()  // Auto-fill other required fields
        .Записать();
    
    // Assert (проверка)
    ЮТест.ОжидаетЧто(Контрагент, "Созданный контрагент")
        .Заполнено()
        .ИмеетТип("СправочникСсылка.Контрагенты")
        .Существует()
        .Свойство("Наименование").Равно(Наименование);
КонецПроцедуры

#КонецОбласти
```

---

### Example 2: Parameterized Test

```bsl
#Область СлужебныйПрограммныйИнтерфейс

Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("СложениеЧисел")
            .СПараметрами(2, 3, 5)
            .СПараметрами(-10, 10, 0)
            .СПараметрами(5, -2, 3)
            .СПараметрами(0, 0, 0);
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура СложениеЧисел(Слагаемое1, Слагаемое2, ОжидаемыйРезультат) Экспорт
    // Arrange (подготовка)
    // Данные поступают из параметров
    
    // Act (действие)
    Результат = ТестируемыйМодуль.Сложить(Слагаемое1, Слагаемое2);
    
    // Assert (проверка)
    ЮТест.ОжидаетЧто(Результат).Равно(ОжидаемыйРезультат, 
        СтрШаблон("Сложение %1 + %2 должно равняться %3", Слагаемое1, Слагаемое2, ОжидаемыйРезультат));
КонецПроцедуры

#КонецОбласти
```

---

### Example 3: Database Check with Predicate

```bsl
#Область СлужебныйПрограммныйИнтерфейс

Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ПроверкаУникальностиАртикула");
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура ПроверкаУникальностиАртикула() Экспорт
    // Arrange (подготовка)
    УникальныйАртикул = ЮТест.Данные().СлучайнаяСтрока(8);
    
    Предикат = ЮТест.Предикат()
        .Реквизит("Артикул").Равно(УникальныйАртикул)
        .Получить();
    
    // Verify uniqueness before test
    ЮТест.ОжидаетЧтоТаблицаБазы("Справочник.Товары", "Артикул уникален до теста")
        .НеСодержитЗаписей(Предикат);
    
    // Act (действие)
    Товар = ЮТест.Данные().КонструкторОбъекта("Справочник.Товары")
        .Установить("Артикул", УникальныйАртикул)
        .ФикцияОбязательныхПолей()
        .Записать();
    
    // Assert (проверка)
    ЮТест.ОжидаетЧтоТаблицаБазы("Справочник.Товары", "Товар записан в базу")
        .СодержитЗаписей(Предикат);
    
    ЮТест.ОжидаетЧто(Товар.Артикул).Равно(УникальныйАртикул);
КонецПроцедуры

#КонецОбласти
```

---

### Example 4: Document with Tabular Section

```bsl
#Область СлужебныйПрограммныйИнтерфейс

Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ПроведениеДокументаПриходТовара");
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура ПроведениеДокументаПриходТовара() Экспорт
    // Arrange (подготовка)
    // Create test товары
    Товар1 = ЮТест.Данные().КонструкторОбъекта("Справочник.Номенклатура")
        .ФикцияОбязательныхПолей()
        .Записать();
    
    Товар2 = ЮТест.Данные().КонструкторОбъекта("Справочник.Номенклатура")
        .ФикцияОбязательныхПолей()
        .Записать();
    
    Количество1 = 10;
    Цена1 = 100;
    Количество2 = 5;
    Цена2 = 200;
    
    // Act (действие)
    Документ = ЮТест.Данные().КонструкторОбъекта("Документ.ПриходТовара")
        .ФикцияОбязательныхПолей()  // Auto-fill header fields
        .ТабличнаяЧасть("Товары")
            .ДобавитьСтроку()
                .Установить("Номенклатура", Товар1)
                .Установить("Количество", Количество1)
                .Установить("Цена", Цена1)
            .ДобавитьСтроку()
                .Установить("Номенклатура", Товар2)
                .Установить("Количество", Количество2)
                .Установить("Цена", Цена2)
        .Провести(Истина);  // Post and return object
    
    // Assert (проверка)
    ЮТест.ОжидаетЧто(Документ, "Проверка документа")
        .Заполнено()
        .ИмеетТип("ДокументСсылка.ПриходТовара")
        .Свойство("Проведен").ЭтоИстина()
        .Свойство("Товары").ИмеетДлину(2)
        .Свойство("Товары[0].Номенклатура").Равно(Товар1)
        .Свойство("Товары[0].Количество").Равно(Количество1)
        .Свойство("Товары[0].Цена").Равно(Цена1)
        .Свойство("Товары[0].Сумма").Равно(Количество1 * Цена1)
        .Свойство("Товары[1].Номенклатура").Равно(Товар2)
        .Свойство("Товары[1].Количество").Равно(Количество2)
        .Свойство("Товары[1].Цена").Равно(Цена2)
        .Свойство("Товары[1].Сумма").Равно(Количество2 * Цена2);
КонецПроцедуры

#КонецОбласти
```

---

### Example 5: Using Event Handlers

```bsl
#Область СлужебныйПрограммныйИнтерфейс

Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ТестСОбщимиДанными1")
        .ДобавитьТест("ТестСОбщимиДанными2");
КонецПроцедуры

// Setup: runs once before all tests
Процедура ПередВсемиТестами() Экспорт
    // Create shared test контрагент
    ТестовыйКонтрагент = ЮТест.Данные().КонструкторОбъекта("Справочник.Контрагенты")
        .Установить("Наименование", "Тестовый контрагент для всех тестов")
        .ФикцияОбязательныхПолей()
        .Записать();
    
    // Store in context for use in tests
    ЮТест.Контекст().УстановитьЗначение("ОбщийКонтрагент", ТестовыйКонтрагент);
КонецПроцедуры

// Cleanup: runs once after all tests
Процедура ПослеВсехТестов() Экспорт
    // Get shared контрагент and delete
    Контрагент = ЮТест.Контекст().Значение("ОбщийКонтрагент");
    Если ЗначениеЗаполнено(Контрагент) Тогда
        Попытка
            Контрагент.ПолучитьОбъект().Удалить();
        Исключение
            // Ignore deletion errors in cleanup
        КонецПопытки;
    КонецЕсли;
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура ТестСОбщимиДанными1() Экспорт
    // Arrange
    Контрагент = ЮТест.Контекст().Значение("ОбщийКонтрагент");
    
    // Act
    Документ = ЮТест.Данные().КонструкторОбъекта("Документ.Счет")
        .Установить("Контрагент", Контрагент)
        .ФикцияОбязательныхПолей()
        .Записать();
    
    // Assert
    ЮТест.ОжидаетЧто(Документ.Контрагент).Равно(Контрагент);
КонецПроцедуры

Процедура ТестСОбщимиДанными2() Экспорт
    // Arrange
    Контрагент = ЮТест.Контекст().Значение("ОбщийКонтрагент");
    
    // Act
    Документ = ЮТест.Данные().КонструкторОбъекта("Документ.Накладная")
        .Установить("Контрагент", Контрагент)
        .ФикцияОбязательныхПолей()
        .Записать();
    
    // Assert
    ЮТест.ОжидаетЧто(Документ.Контрагент).Равно(Контрагент);
КонецПроцедуры

#КонецОбласти
```

---

### Example 6: Document Movements Test

```bsl
#Область СлужебныйПрограммныйИнтерфейс

Процедура ИсполняемыеСценарии() Экспорт
    ЮТТесты
        .ДобавитьТест("ФормированиеДвиженийПоРегистру");
КонецПроцедуры

#КонецОбласти

#Область Тесты

Процедура ФормированиеДвиженийПоРегистру() Экспорт
    // Arrange (подготовка)
    // Create empty document
    Документ = ЮТест.Данные().СоздатьДокумент("Документ.ПриходнаяНакладная");
    
    // Act (действие)
    // Generate movements with Фикция for dimensions
    ЮТест.Данные().КонструкторДвижений(Документ, "ОстаткиТоваров")
        .ДобавитьСтроку()
            .ФикцияРеквизитов("Номенклатура, Склад")  // Mock dimensions
            .Установить("Количество", 10)  // Specific resource value
        .ДобавитьСтроку()
            .ФикцияРеквизитов("Номенклатура, Склад")
            .Установить("Количество", 5)
        .Записать();
    
    // Assert (проверка)
    Движения = Документ.Движения.ОстаткиТоваров.Выгрузить();
    
    ЮТест.ОжидаетЧто(Движения).ИмеетДлину(2);
    ЮТест.ОжидаетЧто(Движения[0].Количество).Равно(10);
    ЮТест.ОжидаетЧто(Движения[1].Количество).Равно(5);
    ЮТест.ОжидаетЧто(Движения).КаждыйЭлементСодержитСвойство("Номенклатура");
    ЮТест.ОжидаетЧто(Движения).КаждыйЭлементСодержитСвойство("Склад");
КонецПроцедуры

#КонецОбласти
```

---

## Agent Checklist

**Before completing test creation, verify ALL items:**

### Pre-Creation Validation
- [ ] **Project format detected** (EDT or DESIGNER) via config file OR asked user
- [ ] Correct file extension determined (.xml for DESIGNER, .mdo for EDT)
- [ ] Module naming follows convention (prefix + name + suffix)
- [ ] Directory structure correct: `tests/src/CommonModules/[Name]/`
- [ ] Location validated (not in wrong directory)

### File Creation
- [ ] **Directory structure** created correctly:
  - [ ] IF DESIGNER: `[Module]/Ext/` folder exists
  - [ ] IF EDT: NO Ext/ folder (direct Module.bsl in module dir)
- [ ] **Module.bsl** created in correct location:
  - [ ] IF DESIGNER: `tests/src/CommonModules/[Module]/Ext/Module.bsl`
  - [ ] IF EDT: `tests/src/CommonModules/[Module]/Module.bsl`
- [ ] **Metadata file** created with correct format:
  - [ ] IF DESIGNER: `.xml` file in `CommonModules/` root with `<MetaDataObject>` schema
  - [ ] IF EDT: `.mdo` file inside `CommonModules/[Module]/` with `<mdclass:CommonModule>` schema
- [ ] UUID generated for new metadata file (UUID v4 format)
- [ ] Flags in metadata file match tested module type
- [ ] Module registered in Configuration with **correct extension**

### Build and Run
- [ ] Project built successfully after test creation
- [ ] Syntax check passed (check_syntax_designer_modules executed, no ERROR)
- [ ] Test executed after build
- [ ] Test results verified (passed/failed)
- [ ] If MCP errors occurred → logs checked at `${workspaceFolder}/logs/yaxunit-mcp-log.log`

### Test Structure
- [ ] `ИсполняемыеСценарии()` procedure present
- [ ] All tests registered with `.ДобавитьТест()`
- [ ] Test procedure names match registration exactly
- [ ] All test procedures are `Экспорт`
- [ ] Fluent interface used for registration

### Test Implementation
- [ ] Each test follows Arrange-Act-Assert structure
- [ ] Test data uses `.Фикция()` where appropriate (not excessive hardcoding)
- [ ] Assertions use `ЮТест.ОжидаетЧто()` with fluent interface
- [ ] Database checks use `ЮТест.ОжидаетЧтоТаблицаБазы()` where needed
- [ ] Predicates built correctly with `.Получить()` at end

### Integration
- [ ] If using metadata → validated via 1C_BSL_SKILL
- [ ] If project requires → comment blocks added per project_bsl_rules
- [ ] UTF-8 encoding for all files with Russian text
- [ ] Registry updated if project requires

### STOP Conditions (DO NOT PROCEED if any true)
- [ ] **Project format not detected and user not asked**
- [ ] **Wrong file extension used** (.mdo in DESIGNER or .xml in EDT)
- [ ] **Wrong directory structure** (Ext/ folder in EDT or missing Ext/ in DESIGNER)
- [ ] **Wrong metadata location** (inside module dir for DESIGNER or in root for EDT)
- [ ] **Wrong metadata schema** (`<mdclass>` for DESIGNER or `<MetaDataObject>` for EDT)
- [ ] Module naming incorrect or doesn't follow convention
- [ ] Files created in wrong location (not in tests/src/CommonModules)
- [ ] Metadata file missing for new module
- [ ] Module not registered in Configuration
- [ ] Test registered but procedure missing or name mismatch
- [ ] Excessive hardcoded values instead of .Фикция()
- [ ] Project not built after test creation
- [ ] Syntax check not run or ERROR found (check_syntax_designer_modules)
- [ ] Test not executed after build
- [ ] MCP errors not investigated via log file

---

## Summary: The Absolute Rules

1. **ALWAYS** detect project format (EDT vs DESIGNER) before creating files
2. **ALWAYS** use correct file extension (.xml for DESIGNER, .mdo for EDT)
3. **ALWAYS** use correct directory structure:
   - DESIGNER: metadata in root, code in `[Module]/Ext/Module.bsl`
   - EDT: metadata inside module dir, code in `[Module]/Module.bsl`
4. **ALWAYS** use correct metadata schema:
   - DESIGNER: `<MetaDataObject>` with verbose namespaces
   - EDT: `<mdclass:CommonModule>` compact format
5. **NEVER** create tests outside `tests/src/CommonModules`
6. **ALWAYS** use correct naming: `[Префикс]_[ИмяОбъекта][_Суффикс]`
7. **ALWAYS** create both Module.bsl and metadata file with correct extension and location
8. **ALWAYS** register module in Configuration with correct extension
9. **ALWAYS** include `ИсполняемыеСценарии()` procedure
10. **ALWAYS** use fluent interface for registration and assertions
11. **ALWAYS** follow Arrange-Act-Assert structure
12. **ALWAYS** prefer `.Фикция()` over hardcoded values (unless specific value required)
13. **ALWAYS** use `ЮТест.ОжидаетЧто()` for assertions
14. **ALWAYS** call `.Получить()` at end of predicate chain
15. **ALWAYS** build project after creating test
16. **ALWAYS** run check_syntax_designer_modules() after build (verify no ERROR)
17. **ALWAYS** run test after syntax check passes
18. **ALWAYS** check MCP logs at `${workspaceFolder}/logs/yaxunit-mcp-log.log` on errors
19. **NEVER** skip format detection → ASK USER if unclear
20. **NEVER** mix formats (Ext/ in EDT, no Ext/ in DESIGNER, wrong schemas)

**These rules are ABSOLUTE. Violations produce broken tests that won't run or won't test correctly.**

**When user asks to create test:** Detect format → Create test → Build project → Run syntax check → Run test → Report results

---

*This skill ensures proper YAxUnit test structure and usage of framework API. Follow every rule without exception for successful test implementation.*

