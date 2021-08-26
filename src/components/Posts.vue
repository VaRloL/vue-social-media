<template>
<div>
    <div class="px-10 ma-0">
      <div class="d-flex flex-row">
        <v-avatar class="darkLighterClass mx-2">
          <v-img :src="photo"></v-img>
        </v-avatar>
        <div>
          <p class="text-h5 ma-0">{{post.title}}</p>
          <p class="font-italic text-body-2 ma-0">@{{userId}}</p>
        </div>
      </div>
      <div>
        <p>{{post.body}}</p>
      </div>
    <v-divider dark class="my-5"></v-divider>
    </div>
</div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    props: ["post", "photo", "userId"]
})
</script>