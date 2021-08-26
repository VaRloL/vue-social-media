<template>
  <perfect-scrollbar class="darkClass white--text py-2">
    <Posts :posts="posts" :users="users" :photos="photos"></Posts>    
  </perfect-scrollbar>
</template>

<script lang="ts">
  import Vue from 'vue'
  import axios from 'axios'
  import Posts from '../components/Posts.vue'
  export default Vue.extend({
    name: 'Home',
    data: function(){
      return {
        posts:Array<any>(),
        users:Array<any>(),
        photos:Array<any>()
      }
    },
    components:{
      Posts
    },
    created(){
      axios.get("https://jsonplaceholder.typicode.com/posts")
        .then(r => {
          let lol = r.data.map((x : any)=>{return x})
          lol.forEach((xd:any) => {this.posts.push(xd)})
        })

      axios.get("https://jsonplaceholder.typicode.com/users")
        .then(r => {
          let lol = r.data.map((x:any) => {return x})
          lol.forEach((xd:any) => {this.users.push(xd)})
        })
      axios.get("profilepic.json")
        .then(r => {let lol = r.data.map((x:any) => {return x})
          lol.forEach((xd:any) => {this.photos.push(xd)})
        })
    }
  })
</script>

<style scoped>
.ps {
  height:100%;
}
</style>