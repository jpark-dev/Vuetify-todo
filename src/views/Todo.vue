<template>
  <div class="home">
    <field-add-task />
    <list-tasks
      v-if="$store.state.tasks.length"
    />
    <div
      v-else
      class="no-tasks"
    >
      <v-icon
        size="100"
        color="primary"
      >
        mdi-check
      </v-icon>
      <div class="text-h5 primary--text">
        No tasks
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {
    FieldAddTask: require('@/components/Todo/FieldAddTask.vue').default,
    ListTasks: require('@/components/Todo/ListTasks.vue').default,
  }
}
</script>

<style lang="sass">
  .no-tasks
    position: absolute
    left: 40%
    right: 30%
    opacity: 0.5
</style>