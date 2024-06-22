# Simple_RAG_Qdrant
Описание проекта:
QA-llm ассистент по документам из ГОСТ.

Цель: сократить затрачиваемое время на чтение и анализ ГОСТа.

Задачи: 
1. разработать архитектуру приложения, обеспечивающую взаимодействие пользователя с системой.
2. выбрать модели, которые можно запустить локально
3. собрать и предобработать данные
4. выбрать способ хранения эмбеддингов
5. дообучить языковую модель по обработанным данным
6. провалидировать результат RAG работы модели
7. реализовать тестовое приложение\сайт для демонстрации работы системы

# TODO
  
# Schema
<img src="https://github.com/MaximKondakov/Simple_RAG_Qdrant/assets/85742231/77441332-74af-4380-9179-9f3f6a31abec" width=70% height=70%>

# Finetune llm
Использовать юпитер нотбук файнтюн
unsloth + custom dataset

# Qdrant
<img src="https://github.com/MaximKondakov/Simple_RAG_Qdrant/assets/85742231/a79fa0e2-b20d-4303-ad9a-4c3af3d9f25c" width=70% height=70%>

# Result
```
# Пример запроса
query = "Что такое качество излучения?"

output_text = give_answer_llm_qdrant(query)

print(f"Вопрос: {query}")
print_wrapped(f"RAG ответ:\n{output_text['choices'][0]['text']}")
```

<img src="https://github.com/MaximKondakov/Simple_RAG_Qdrant/assets/85742231/0f647457-a035-414e-ad5c-f24d4386d049" width=100% height=100%>

