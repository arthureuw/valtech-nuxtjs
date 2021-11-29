<template>
  <v-app dark>
    <v-app-bar
      fixed
      app
    >
      <v-spacer/>
      <v-toolbar-title v-text="title"/>
      <v-spacer/>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      title: 'Contact List'
    }
  }
}
</script>
