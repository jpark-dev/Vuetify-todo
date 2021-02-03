<template>
  <div>
    <v-menu
      bottom
      left
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          icon
          v-bind="attrs"
          v-on="on"
        >
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </template>

      <v-list>
        <v-list-item
          v-for="(item, index) in items"
          :key="index"
          @click="handleClick(index)"
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon"></v-icon>
          </v-list-item-icon>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>
    <dialog-delete
      v-if="dialogs.delete"
      :task="task"
      @close="dialogs.delete = false"
    />
    <dialog-edit
      v-if="dialogs.edit"
      :task="task"
      @close="dialogs.edit = false"
    />
  </div>
</template>

<script>
export default {
  props: ['task'],
  components: {
    'dialog-delete': require('@/components/Todo/Dialogs/DialogDelete.vue').default,
    'dialog-edit': require('@/components/Todo/Dialogs/DialogEdit.vue').default,
  },
  data: () => ({
    dialogs: {
      delete: false,
      edit: false,
    },
    items: [
      {
        title: 'Edit',
        icon: 'mdi-pencil',
        click() {
          this.dialogs.edit = true;
        },
      },
      {
        title: 'Due date',
        icon: 'mdi-calendar',
        click() {
          console.log(this.title);
        },
      },
      {
        title: 'Delete',
        icon: 'mdi-delete',
        click() {
          this.dialogs.delete = true;
        },
      },
    ],
  }),
  methods: {
    handleClick(index) {
      this.items[index].click.call(this);
    }
  }
}
</script>
