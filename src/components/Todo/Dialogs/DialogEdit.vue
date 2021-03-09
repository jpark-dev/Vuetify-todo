<template>
  <v-dialog
    :value="true"
    persistent
    max-width="290"
  >
    <v-card>
      <v-card-title class="headline">
        Edit Task?
      </v-card-title>
      <v-card-text>
        Are you sure to edit this awesome task that can change your life?
        <v-text-field
          v-model="taskTitle"
          @keyup.enter="saveTask"
        />
      </v-card-text>
      <v-card-actions>
        <v-spacer />
        <v-btn
          text
          @click="$emit('close')"
        >
          Cancel
        </v-btn>
        <v-btn
          @click="saveTask"
          :disabled="taskTitleInvalid"
          color="red darken-1"
          text
        >
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: ['task'],
  data() {
    return {
      taskTitle: null,
    }
  },
  computed: {
    taskTitleInvalid(){
      return !this.taskTitle || this.taskTitle === this.task.title
    }
  },
  methods: {
    saveTask() {
      if (!this.taskTitleInvalid) {
        const payload = {
        id: this.task.id,
        title: this.taskTitle,
      }
      this.$store.dispatch('updateTaskTitle', payload);
      this.$emit('close');
      this.$vuetify.goTo(0, { duration: 0 });
      }
    },
  },
  mounted() {
    this.taskTitle = this.task.title;
  }
}
</script>

<style>

</style>