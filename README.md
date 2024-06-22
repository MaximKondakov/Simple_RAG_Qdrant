# Simple_RAG_Qdrant
Описание проекта:
Я не люблю читать ГОСТ, поэтому пусть с этим разбирается llm ассистент.

Используемые библиотеки: fitz, json, re, llama_cpp, torch, numpy, spacy, transformers, unsloth, peft, accelerate, bitsandbytes

Цель: сократить затрачиваемое время на чтение и анализ любого ГОСТа.

Задачи: 
- [x]  разработать архитектуру приложения, обеспечивающую взаимодействие пользователя с системой.
- [x]  выбрать модели, которые можно запустить локально
- [x]  собрать и предобработать данные
- [x]  выбрать способ хранения эмбеддингов
- [x]  дообучить языковую модель по обработанным данным
- [ ]  провалидировать результат RAG работы модели
- [ ]  реализовать тестовое приложение\сайт для демонстрации работы системы

# TODO
- [ ] добавить чтение таблиц\рисунков из pdf
- [ ] разделение на семантические чанки
- [ ] добавить в препроцессинг исправление слов (п р и л о ж е н и е -> приложение)
- [ ] сделать диалоговый формат общения с ллм (контекст предыдущих сообщений должен учитываться)
- [ ] собрать Docker compose
- [ ] развернуть Streamlit используя FastAPI

# Схема RAG системы
<img src="https://github.com/MaximKondakov/Simple_RAG_Qdrant/assets/85742231/77441332-74af-4380-9179-9f3f6a31abec" width=70% height=70%>

# Файнтюн llm
Использовать [finetune_llama3_8b.ipynb](https://github.com/MaximKondakov/Simple_RAG_Qdrant/blob/main/finetune_llama3_8b.ipynb). Для файнтюна используется библиотека [Unslot](https://github.com/unslothai/unsloth) , но она работает только на Linux машине. [Датасет](https://github.com/MaximKondakov/Simple_RAG_Qdrant/blob/main/ya_dataset.json) для обучения создается с помощью YandexGPT, скрипт [создания](https://github.com/MaximKondakov/Simple_RAG_Qdrant/blob/main/simple_rag_qdrant.ipynb) находится в секции "Creation dataset for finetune"

# Qdrant
Для поиска эмбеддингов используется скалярное произведение, т.к. косинусное сходство учитывает только разность углов, а скалярное произведение — угол и величину. 

<img src="https://github.com/MaximKondakov/Simple_RAG_Qdrant/assets/85742231/a79fa0e2-b20d-4303-ad9a-4c3af3d9f25c" width=70% height=70%>

# Результат
Для получения инференса модели, должна быть установлена библиотека llama-cpp-python.
```
# Пример запроса
query = "Что такое качество излучения?"

output_text = give_answer_llm_qdrant(query)

print(f"Вопрос: {query}")
print_wrapped(f"RAG ответ:\n{output_text['choices'][0]['text']}")
```

<img src="https://github.com/MaximKondakov/Simple_RAG_Qdrant/assets/85742231/0f647457-a035-414e-ad5c-f24d4386d049" width=100% height=100%>

