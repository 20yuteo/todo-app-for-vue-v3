<template>
    <div v-for="(todo, key) in todos" :key="key">
        <Todo :id="todo.id" :title="todo.title" :isDone="todo.isDone" @doneTodo="doneTodo" />
    </div>
    <TodoSubmit @setTodo="setTodo" />
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'
import Todo from '../components/Todo.vue'
import TodoSubmit from '../components/TodoForm.vue'

type TodoType = {
    id: number
    title: string
    isDone: boolean
}

export default defineComponent({
  components: {
    Todo,
    TodoSubmit
  },

  setup () {
    const todoList: TodoType[] = [
      {
        id: 1,
        title: 'test title01',
        isDone: true
      },
      {
        id: 2,
        title: 'test title02',
        isDone: false
      },
      {
        id: 3,
        title: 'test title03',
        isDone: false
      }
    ]

    const todos = reactive<TodoType[]>(todoList)

    const setTodo = (title: string) => {
      let lastId = todos.length
      lastId++
      todos.push({
        id: lastId,
        title: title,
        isDone: false
      })
    }

    const doneTodo = (id: number) => {
      const doneTodo: TodoType | undefined = todos.find(e => (
        e.id === id
      ))

      if (doneTodo !== undefined) doneTodo.isDone = true

      console.log(todos)
    }

    return {
      todos,
      setTodo,
      doneTodo
    }
  }
})
</script>
