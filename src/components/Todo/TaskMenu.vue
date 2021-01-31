<template>
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
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        title: 'Edit',
        icon: 'mdi-pencil',
        click() {
          console.log(this.title);
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
          console.log(this.title);
        },
      },
    ],
  }),
  methods: {
    handleClick(index) {
      this.items[index].click();
    }
  }
}
</script>

<style>

</style>