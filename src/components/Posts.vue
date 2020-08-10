<template>
  <v-container class="grey lighten-5">
    <v-row no-gutters>
      <v-col v-for="(post,index) in posts" :key="index" cols="12" sm="6">
        <v-card max-width="344" class="pa-2 mx-auto my-3">
          <v-list-item>
            <v-list-item-avatar color="grey"></v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-title class="headline">{{post.title}}</v-list-item-title>
              <v-list-item-subtitle>Posted by Bakhtiyar</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-img v-bind:src="baseUrl+post.image" height="194"></v-img>

          <v-card-text>{{post.content.substr(0,50)}}....</v-card-text>

          <v-card-actions>
            <v-btn text color="deep-purple accent-4">Read more</v-btn>
            <small>{{new Date(post.created_at).toLocaleTimeString()}}</small>
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon>mdi-heart</v-icon>
            </v-btn>
            <v-btn icon>
              <v-icon>mdi-share-variant</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Posts",

  data() {
    return {
      posts: null,
      baseUrl: "http://127.0.0.1:8000",
    };
  },
  mounted() {
    fetch("http://127.0.0.1:8000/api/v1/posts")
      .then((response) => response.json())
      .then((json) => (this.posts = json));
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
