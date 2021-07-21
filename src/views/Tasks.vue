<template>
  <h1 v-if="tasks.length === 0" class="text-white center">Задач пока нет</h1>
  <div v-else>
    <h3 class="text-white">Всего активных задач: {{ activeTasksCount }}</h3>
    <div class="card" v-for="task in tasks" :key="task.id">
      <h2 class="card-title">
        {{task.title}}
        <AppStatus :type="task.status" />
      </h2>
      <p>
        <strong>
          <small>
            {{new Date(task.date).toLocaleDateString()}}
          </small>
        </strong>
      </p>
      <div>
        <button class="btn primary" @click="open(task.id)">Посмотреть</button>
        <button class="btn danger" @click="deleteTask(task.id)">Удалить</button>
      </div>      
    </div>
  </div>
</template>

<script>
import {computed} from 'vue'
import {useStore} from 'vuex'
import {useRouter} from 'vue-router'
import AppStatus from '../components/AppStatus'

export default {
  setup() {
    const store = useStore()
    const router = useRouter()
    const tasks = computed(() => store.getters.tasks)
    const activeTasksCount = computed(() => store.getters.activeTasksCount)
    const deleteTask = (id) => store.dispatch("deleteTask", id) 

    return {
      tasks, activeTasksCount,deleteTask,
      open: id => router.push(`/task/${id}`)  
    }
  },
  components: {AppStatus}
}
</script>
