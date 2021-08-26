<template>
  <v-app dark>
    <navDraw/>
    <v-main>
      <div class="d-flex flex-row">
        <router-view></router-view>
      </div>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import navDraw from './components/navDraw.vue';
export default Vue.extend({
  name: 'App',
  components:{
    navDraw
  },
  data: () => ({
    //
  }),
});
</script>

<style>
.darkClass {
  background-color:#121212;
}

.darkLighterClass {
  background-color:#1f1f1f;
}
</style>