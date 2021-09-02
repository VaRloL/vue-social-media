<template>
  <perfect-scrollbar class="pa-5 darkClass">
    <!--USER-RELATED STUFF-->
    <div v-if="userInfo != undefined">
      <div>
        <div>
          <v-img
            max-height="200"
            src="https://pbs.twimg.com/profile_banners/1257109383584133120/1625421810/1500x500"
          ></v-img>
        </div>
        <div class="d-flex flex-row">
          <v-avatar
            size="140"
            color="grey darken-4"
            style="margin-top: -50px; margin-left: 20px"
            ><v-avatar size="128"><v-img v-if="pfp != ''" :src="pfp"></v-img></v-avatar
          ></v-avatar>
          <div>
            <p class="text-h4 ml-3 mt-2 mb-0 white--text font-italic">
              @{{ userInfo.username }}
            </p>
            <p class="text-h6 grey--text ml-3 ma-0">{{ userInfo.name }}</p>
          </div>
          <v-btn class="ml-auto my-auto mr-10" dark>Follow+</v-btn>
        </div>
        <div class="d-flex flex-row ml-5 mt-5">
            <v-icon dark>mdi-map-marker-outline</v-icon>
            <p class="white--text" style="margin-top:auto;margin-bottom:auto;">{{userInfo.address.city}}</p>
        </div>
        <div class="d-flex flex-row ml-5">
            <v-icon dark>mdi-web</v-icon>
            <p class="white--text" style="margin-top:auto;margin-bottom:auto;">{{userInfo.website}}</p>
        </div>
        <v-divider dark class="ma-5"></v-divider>
      </div>
    </div>
    <!---POSTS--->
    <div v-if="userPosts.length != 0" class="white--text">
        <posts v-for="post in userPosts" :key="post.id" :post="post" :photo="pfp" :userId="userInfo"/>
    </div>
    </perfect-scrollbar>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";
import posts from '../components/Posts.vue'

export default Vue.extend({
  data: function () {
    return {
      userInfo: undefined,
      pfp: "",
      userPosts: Array<any>()
    };
  },
  components: {
      posts
  },
  created() {
    if (this.$route.params.userId != "") {
      axios
        .get(
          "https://jsonplaceholder.typicode.com/users/" +
            this.$route.params.userId
        )
        .then((r) => (this.userInfo = r.data));

      axios.get("/profilepic.json").then((r) => {
        let x = r.data.find(
          (lol: any) => lol.UserId == this.$route.params.userId
        );
        this.pfp = x.pfp;
      });

      axios.get("https://jsonplaceholder.typicode.com/posts")
      .then(r => {
          r.data.forEach((element:any) => {
              if(element.userId == this.$route.params.userId){
                  this.userPosts.push(element)
              }
          });
      })
    }
  },
});
</script>