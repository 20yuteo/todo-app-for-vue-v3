<template>
    <form action="" @submit.prevent="handleSubmit">
        <label for="title">
            Title
        </label>
        <input type="text" v-model="title" />
        <input type="submit">
    </form>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  emits: ['setTodo'],
  setup (props, { emit }) {
    const title = ref('')

    const handleSubmit = () => {
      emit('setTodo', title.value)
      title.value = ''
    }

    return {
      title,
      handleSubmit
    }
  }
})
</script>
