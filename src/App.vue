<template>
  <v-app dark>
    <navDraw/>
    <v-main class="darkClass">
      <v-row>
        <router-view></router-view>
      </v-row>
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

.post{
  border:1px solid #313131;
}

.ps{
  width:100%;
}
</style>