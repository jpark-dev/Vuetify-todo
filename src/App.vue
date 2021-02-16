<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :mobile-breakpoint="768"
      app
    >
      <v-img
        class="pa-4"
        src="coding-bg.jpg"
        height="150"
        gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
      >
        <v-avatar
          class="mb-2"
          size="70"
        >
          <img
            src="pika.webp"
            alt="Jason Park"
          >
        </v-avatar>
        <div class="white--text text-subtitle-1 font-weight-bold">
          Pika Chu
        </div>
        <div class="white--text text-subtitle-2">
          chu@pika.com
        </div>
      </v-img>
      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      class="pt-2"
      app
      color="primary"
      dark
      src="coding-bg.jpg"
      prominent
      height="150"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon
            @click="drawer = !drawer"
          />
          <v-spacer></v-spacer>
          <search />
        </v-row>
        <v-row>
          <v-app-bar-title class="text-h4 ml-4">
            Vuetify Todo
          </v-app-bar-title>
        </v-row>
        <v-row>
          <live-date-time />
        </v-row>
      </v-container>

    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snackbar />
    </v-main>

  </v-app>
</template>

<script>
  export default {
    data: () => ({
      drawer: true,
      items: [
        { title: 'Todo', icon: 'mdi-format-list-checks', to: '/' },
        { title: 'About', icon: 'mdi-help-box', to: '/about' },
      ],
    }),
    components: {
      'search': require('@/components/Tools/Search.vue').default,
      'live-date-time': require('@/components/Tools/LiveDateTime.vue').default,
      'snackbar': require('@/components/Common/Snackbar.vue').default,
    }
  }
</script>

<style lang="sass">
  .header-container
    max-width: none !important,
</style>
