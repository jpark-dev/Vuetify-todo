<template>
  <div class="home">
    <field-add-task />
    <list-tasks
      v-if="$store.state.tasks.length"
    />
    <no-tasks
      v-else
    />
    <button-done-sorting
      v-if="$store.state.sorting"
    />
  </div>
</template>

<script>
export default {
  name: 'Home',
  components: {
    FieldAddTask: require('@/components/Todo/FieldAddTask.vue').default,
    ListTasks: require('@/components/Todo/ListTasks.vue').default,
    NoTasks: require('@/components/Todo/NoTasks.vue').default,
    ButtonDoneSorting: require('@/components/Todo/ButtonDoneSorting.vue').default,
  }
}
</script>
