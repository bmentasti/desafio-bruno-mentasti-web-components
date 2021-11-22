<template>
  <v-app>
    <v-main>
      <Reserva/>
    </v-main>
  </v-app>
</template>

<script>
import Reserva from "./components/Reserva";

export default {
  name: 'App',

  components: {
    Reserva,
  },
};
</script>
