<template>
  <span :class="['status', className]">{{ text }}</span>
</template>

<script>
import {watch, ref} from 'vue'
export default {
  props: {
    type: {
      type: String,
      validator(value) {
        return ['active', 'done', 'pending', 'cancelled'].includes(value)
      }
    }
  },
  setup(props) {
    const classesMap = {
      active: 'primary',
      cancelled: 'danger',
      done: 'primary',
      pending: 'warning'
    }

    const textMap = {
      active: 'Активен',
      cancelled: 'Отменен',
      done: 'Завершен',
      pending: 'Выполняется'
    }

    const className = ref(classesMap[props.type])
    const text = ref(textMap[props.type])

    watch(props, val => {
      className.value = classesMap[val.type]
      text.value = textMap[val.type]
    })

    return {
      className,
      text
    }
  }
}
</script>

<style scoped>
  .status {
    font-size: 0.8rem;
    border: 1px solid #eee;
    border-radius: 15px;
    padding: 0 .5rem;
}

.status.primary {
    border-color: rgb(0, 222, 0);
    color: rgb(0, 222, 0);
}

.status.danger {
    border-color: rgb(255, 0, 0);
    color: rgb(255, 0, 0);
}

.status.warning {
    border-color: rgb(255, 166, 0);
    color: rgb(255, 166, 0);
}
</style>