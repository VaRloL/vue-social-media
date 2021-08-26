<template>
<div>
    <div v-for="items, index of posts" :key="index" class="px-10 ma-0">
      <div class="d-flex flex-row">
        <v-avatar class="darkLighterClass mx-2">
          <v-img :src="findPicture(items.userId)"></v-img>
        </v-avatar>
        <div>
          <p class="text-h5 ma-0">{{items.title}}</p>
          <p class="font-italic text-body-2 ma-0">@{{findId(items.userId)}}</p>
        </div>
      </div>
      <div>
        <p>{{items.body}}</p>
      </div>
    <v-divider dark class="my-5"></v-divider>
    </div>
</div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    props: ["posts", "photos", "users"],
    methods:{
      findId(id : number){
        let x = this.users.find((userId: any) => userId.id === id)
        return x.username
      },
      findPicture(id:number){
        let x = this.photos.find((userId : any) => userId.UserId === id)
        return x.pfp
      }
    }
})
</script>