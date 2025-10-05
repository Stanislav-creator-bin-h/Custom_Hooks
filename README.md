 Todo List Application (Lab 4: Fetching Data. Custom Hooks)
🔗 Vercel Deployment (https://custom-hooks-topaz.vercel.app/)
🔗 GitHub Repository (https://github.com/Stanislav-creator-bin-h/Custom_Hooks.git)

✨ Функціональність та Ключові Особливості
Додаток реалізує повноцінний Todo List з використанням асинхронної взаємодії з API та повною інкапсуляцією логіки в кастомному хуку.

Асинхронне отримання даних: Початкове завантаження завдань відбувається через useEffect та GET /todos (DummyJSON).

CRUD Операції з API: Додавання, перемикання статусу та видалення завдань супроводжуються відповідними API запитами (POST, PUT, DELETE).

Кастомний Хук useTodos: Вся логіка стану (todos, isLoading, error) та асинхронні функції-мутації ін капсульовані в одному хуку.

Обробка Станів: Відображається індикатор завантаження (isLoading) та повідомлення про помилку (error), отримане під час взаємодії з API.

Типізація: Весь проєкт написаний на TypeScript з чітким визначенням інтерфейсів, що забезпечує високу надійність.

🌳 Схема Компонентів та Потік Даних (Component Tree + Data Flow)
Ця діаграма відображає, як кастомний хук стає єдиним джерелом даних та функціональності, повністю звільняючи компоненти від логіки Fetching.

App.tsx
│
└── TodoList.tsx
      │ 
      │ (TodoList споживає всі дані та колбеки, але не містить основного стану)
      │
      ├── (useTodos Hook)
      │     (Містить Стан: todos, isLoading, error)
      │     (Містить Функції: addTodo, deleteTodo, toggleTodo)
      │     (Виконує Fetch API: GET, POST, PUT, DELETE)
      │
      ├── AddTodoForm.tsx
      │     (Локальний Стан: newTodo)
      │     ↑ onAddTodo(text: string)
      │ 
      └── TodoItem.tsx
            │  (Props: todo {id, text, completed}, onToggleComplete, onDeleteTodo)
            │  (Локальний Стан: isEditing: boolean)
            │ 
            ├── [Checkbox] onChange -> onToggleComplete(id)
            └── [Delete Button] onClick -> onDeleteTodo(id)