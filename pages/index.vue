<template>
  <div>
    <h1 v-if="this.data_coba === 'asik'">Vue is awesome!</h1>
    <h1 v-else>belajar lagi yaa</h1>



<li v-for="item in this.posts">
  {{ item.id }}
   {{ item.username }}
</li>
    

  <!-- id : {{this.posts[0].id}}
  username : {{this.posts[0].username}}
  password : {{this.posts[0].password}} -->

  </div>
</template>

<script>
export default {
  name: 'IndexPage',
    data() {
    return {
      items:["kucing","anjing","ayam"],
    data_coba: "gak asik",
      posts: [],
      sales: [
        [{ Year: 2018 }, { Year: 2018 }],
        [{ Year: 2017 }, { Year: 2017 }],
      ],
    };
  },

    mounted() {
    console.log("test");
    //fething ke Rest API
    this.$axios
      .get("/api/user")
      .then((response) => {
        //assign response ke state "posts"
        this.posts = response.data.data;
        console.log(this.posts);
        console.log(this.posts[0].username);
      })
      .catch((error) => {
        console.log(error.response.data);
      });
  },


  
}
</script>
