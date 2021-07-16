<template>
  <form class="card" @submit.prevent="submit">
    <h1>Создать новую задачу</h1>
    <div class="form-control">
      <label for="title">Название</label>
      <input type="text" id="title" v-model="title">
    </div>

    <div class="form-control">
      <label for="date">Дата дэдлайна</label>
      <input type="date" id="date" v-model="date">
    </div>

    <div class="form-control">
      <label for="description">Описание</label>
      <textarea id="description" v-model="description"></textarea>
    </div>

    <button class="btn primary" :disabled="!isValid">Создать</button>
  </form>
</template>


<script>
import {ref, computed} from 'vue'
import {useStore} from 'vuex'
import {useRouter} from 'vue-router'

export default {
  setup() {
    const store = useStore()
    const router = useRouter()
    const title = ref('')
    const date = ref(null)
    const description = ref('')

    const submit = () => {
      const newTask = {
        id: Date.now().toString(),
        title: title.value,
        date: new Date(date.value).setHours(23,59,59,999),
        description: description.value,
        status: 'active'
      }

      store.dispatch('createTask', newTask)
      router.push('/')
    }

    const isValid = computed(() => {
      return title.value !== '' &&
             date.value && description.value !== ''
    })

    return {
      submit,
      title,
      date,
      description,
      isValid,
    }
  }
}
</script>

<style scoped>
.form-control {
    position: relative;
    margin-bottom: 0.5rem;
}

.form-control input,
.form-control select,
.form-control textarea{
    font-family: Arial, Helvetica, sans-serif;
    margin: 0;
    outline: none;
    border: 2px solid rgb(216, 216, 216);
    display: block;
    width: 100%;
    padding: 0.5rem 1.5rem;
    border-radius: 3px;
    font-size: 1rem;
    resize: none;
}

.form-control label {
    display: block;
    margin: 0 0 0.3rem 0.3rem;
}

.form-control input:active,
.form-control input:focus {
    border: 2px solid rgb(0, 222, 0);
}
</style>