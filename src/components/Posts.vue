<template>
<div>
  <div v-if="hidden==false" class="d-flex flex-column rounded post mb-2 pa-3">
    <div class="d-flex flex-row">
      <v-avatar class="mr-3">
        <v-img :src="photo"></v-img>
      </v-avatar>
      <div class="d-flex flex-column ">
        <p class="text-h5 ma-0">{{post.title}}</p>
        <a @click="$router.push('/profile/'+userId.id).catch(err => {})">@{{userId.username}}</a>
      </div>

      <v-menu>
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-on="on" v-bind="attrs" dark icon outlined class="ml-auto"><v-icon>mdi-chevron-down</v-icon></v-btn>
        </template>
        <v-list class="pa-0" dark>
          <v-list-item>
            <v-btn plain @click="hidden=true" block dark>Hide Content</v-btn>
          </v-list-item>
        </v-list>
      </v-menu>
    </div>

    <div>
      <p>{{post.body}}</p>
    </div>
  </div>
  <v-divider dark class="ma-2" v-if="hidden==false"></v-divider>
  <!--If element is hidden, show this instead-->
  <div v-if="hidden == true" class="d-flex flex-column align-center white--text">
    <p>Sorry about that, we will hide this for you.</p>
    <p>Did you make a mistake?</p>
    <v-btn dark outlined @click="hidden=false" width="200px">Show Content</v-btn>
    <v-divider class="ma-2" dark></v-divider>
  </div>
  
</div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    props: ["post", "photo", "userId"],
    data: function() {
      return {
        hidden:false
      }
    }
})
</script>
