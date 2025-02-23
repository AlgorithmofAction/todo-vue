# Веб-приложение ToDo (Vue.js + Tailwind CSS)

> (Английская версия сайта)

## Main Design

<img src="https://github.com/noneandundefined/todo-vue/blob/main/docs/images/design-todo.jpg" width="500" align="center"></img>

Это веб приложение представляет собой простое веб-приложение ToDo, разработанное с использованием Vue.js для реактивности и компонентной архитектуры, Tailwind CSS для стилизации и JavaScript для логики приложения. Изначально задачи ToDo хранятся в LocalStorage браузера.

> [!NOTE] > **Статус** В настоящее время находится на этапе статического макета

## Функциональность

- **Создание задач ToDo:** Добавление новых задач с названиями, статусами, владельцами, приоритетами и диапазонами дат.
- **Просмотр задач ToDo:** Отображение задач в табличном формате.
- **Фильтрация задач ToDo:** Фильтрация задач по статусу (Done, In Progress, Planning, Canceled).
- **Поиск задач ToDo:** Поиск задач по названию.
- **Сохранение данных:** Хранение задач ToDo в LocalStorage.
- **Локализация:** Поддержка нескольких языков (английский, русский).
- **Расширенные функции (В будущем):** Аутентификация пользователей, назначение задач, сроки выполнения, уведомления.

## Планируемая Структура Данных (JSON)

```json
[
 {
  "id": 1,
  "todo_title": "Купить продукты",
  "status": "In Progress", // Done | Canceled | Planning
  "owner": "Ivan Ivanov",
  "priority": "Hihg", // Low | Medium
  "startDate": "Sep 16, 2024",
  "endDate": "Sep 18, 2024"
 },
 ...
]
```

## Ресурсы

### Поиск иконков (Обязательно в svg формате -> после чего адаптировать в vue формат)

- Иконки нужно искать на сайте - [heroicons](https://heroicons.com/solid)
- Или тут [material ui](https://pictogrammers.com/library/mdi/)
- Хранить иконки в папки constants/ -> svgs/ [например DeleteIcon.vue]

DeleteIcon.vue (ниже показан метод на Vue)

```vue
<script>
export default {
	props: {
		fill: {
			type: String,
			required: true,
		},
		size: {
			type: Number,
			default: 24,
		},
		style: {
			type: Object,
			default: () => ({}), // Important: default value should be a function returning an object
		},
		class: {
			type: String,
			default: '',
		},
		onClick: {
			type: Function,
			default: null, // Or undefined if you prefer
		},
	},
};
</script>

<template>
	<svg
		xmlns="http://www.w3.org/2000/svg"
		:class="class"
		viewBox="0 0 24 24"
		:fill="fill"
		:style="style"
		:width="size"
		:height="size"
		@click="onClick"
	>
		<path
			d="M19,4H15.5L14.5,3H9.5L8.5,4H5V6H19M6,19A2,2 0 0,0 8,21H16A2,2 0 0,0 18,19V7H6V19Z"
		/>
	</svg>
</template>

<style scoped>
/*  Scoped styles for the component, if needed */
</style>
```

Использование

```vue
<script>
import DeleteIcon from './DeleteIcon.vue';

export default {
	components: {
		DeleteIcon,
	},
	methods: {
		handleDelete() {
			console.log('Delete icon clicked!');
		},
	},
};
</script>

<template>
	<div>
		<DeleteIcon
			fill="#000" // Обязательно
			size="29" // Необязательно
			class="bg-[#fff]" // Необязательно
            style={background: "#fff"} // Необязательно
			@click="handleDelete" // Необязательно
		/>
	</div>
</template>
```

## С чего начать

1. Начни с реализации макета как на картинке выше, разбей все на компоненты - header | в папку ui помести RowTable.vue DataTable.vue | вынеси модальные окна также в компоненты | что по считаешь нужным вынеси, я если что посмотрю и подкоректирую

> [!WARNING]
> DataTable.vue это название колонок и в tr будет кмпонент RowTable.vue это сами данные задач

> [!WARNING]
> Если будут вопросы по этому плану или ошибки по фукнционалу пиши
