<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
      <h1>Phonebook</h1>
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main class="mt-5">
      <Phonebook />
    </v-main>
  </v-app>
</template>

<script>
import Phonebook from "./components/Phonebook";

export default {
  name: "App",

  components: {
    Phonebook
  },

  data: () => ({
  })
};
</script>
