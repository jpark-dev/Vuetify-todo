<template>
  <v-list
    class="pt-0"
    flat
  >
    <draggable
      :list="$store.getters.tasksFiltered"
      handle=".handle"
    >
      <task
        v-for="task in $store.getters.tasksFiltered"
        :key="task.id"
        :task="task"
      />
    </draggable>
  </v-list>
</template>

<script>
import draggable from "vuedraggable";

import Task from './Task.vue'
export default {
  components: {
    Task,
    draggable,
  }
}
</script>
