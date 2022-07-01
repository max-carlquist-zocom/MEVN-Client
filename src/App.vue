<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <button @click="getPosts">get Posts</button>
    <div v-for="post in posts" :key="post.id">
      <h3>{{ post.title }}</h3>
      <small>{{ post.author }}</small>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import axios from 'axios';

export default {
  data() {
    return {
      posts: []
    }
  },
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    async getPosts() {
      const res = await axios.get('http://localhost:1337/posts');
      const data = await res.data;
      this.posts = data;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
