<template>
    <div>
        <span>
          id: {{ id }}
        </span>
        <span>
          title: {{ title }}
        </span>
        <span style="color: red">
          {{ isDone ? 'done' : null }}
        </span>
        <input v-if="!isDone" type="checkbox" @change="handleChange" />
    </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  props: {
    id: Number,
    title: String,
    isDone: Boolean
  },
  emits: ['doneTodo'],

  setup (props, { emit }) {
    const checkedTodo = []

    const handleChange = () => {
      emit('doneTodo', props.id)
    }

    return {
      checkedTodo,
      handleChange
    }
  }
})
</script>
