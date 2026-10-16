
# Диаграммы

## Диаграмма последовательности


```mermaid
sequenceDiagram
    actor HR as HR
    participant System as System
    participant Model as MLModel

    HR->>System: Загрузить резюме кандидата
    System->>System: Проверить формат файла
    System->>System: Извлечь текст резюме
    System->>Model: Передать текст резюме для анализа
    Model-->>System: Вернуть навыки, образование и опыт
    System->>System: Сравнить с требованиями вакансии
    System-->>HR: Показать результат анализа
```

## Диаграмма классов

```mermaid
classDiagram
    class User {
        +id: int
        +name: String
        +role: String
        +uploadResume()
        +viewAnalysisResult()
    }

    class Resume {
        +id: int
        +fileName: String
        +format: String
        +text: String
        +skills: List
        +education: List
        +experience: List
        +validateFormat()
        +extractText()
    }

    class Vacancy {
        +id: int
        +title: String
        +requiredSkills: List
        +requiredEducation: List
        +requiredExperience: List
        +getRequirements()
    }

    class MLModel {
        +modelVersion: String
        +analyzeResume(text)
        +extractEntities()
    }

    class AnalysisResult {
        +id: int
        +matchedSkills: List
        +missingRequirements: List
        +matchScore: float
        +recommendations: List
        +generateResult()
    }

    User "1" --> "*" Resume : uploads
    Resume --> MLModel : processed by
    Resume "1" --> "*" AnalysisResult : analyzed in
    Vacancy "1" --> "*" AnalysisResult : compared in
    MLModel --> AnalysisResult : generates
```
