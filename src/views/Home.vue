<template>
  <perfect-scrollbar v-if="posts.length != 0" class="darkClass white--text py-5 px-5" :style="{'height': '${vuetify.breakpoint.height}px'}">
    <Posts v-for="post in posts" :key="post.id" :photo="findPicture(post.userId)"
    :userId="findId(post.userId)" :post="post"></Posts>    
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
    },
    methods:{
      findId(id : number){
        let x = this.users.find((userId: any) => userId.id === id)
        return x
      },
      findPicture(id:number){
        let x = this.photos.find((userId : any) => userId.UserId === id)
        return x.pfp
      }
    }
  })
</script>

<style scoped>
.ps{
  width:100%;
}
</style>