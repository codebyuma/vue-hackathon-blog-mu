<template>
  <div id="app">
    <AddPost :submit="submit"/>
    <h2>The Posts:</h2>
    <Post v-for="post in posts" :thePost="post" :remove="remove" :edit="edit" :toggle="toggleEditting" :isEditting="isEditting" :key="post.id" />
  </div>
</template>

<script>
import Post from "./components/post.vue";
import AddPost from "./components/addPost.vue";
import { reject } from "ramda";

export default {
  name: "app",
  components: {
    Post,
    AddPost
  },
  methods: {
    submit(value) {
      this.posts.push({ ...value, id: this.postCount });
      this.postCount++;
    },
    remove(postId) {
      const findPostToDelete = post => post.id === postId;
      this.posts = reject(findPostToDelete, this.posts);
    },
    edit(post) {
      console.log("post", post);
    },
    toggleEditting(id) {
      this.isEditting = id;
    }
  },
  data: () => {
    const posts = [
      {
        id: 0,
        author: "@vFitzgerald",
        title: "Quod Ducimus Omnis",
        label: "science"
      },
      {
        id: 1,
        author: "@mPalmer",
        title: "Vero Eius Laboriosam Ex Repudiandae",
        label: "math"
      },
      {
        id: 2,
        author: "@mDean",
        title: "Magnam Odit",
        label: "science"
      }
    ];
    return {
      posts,
      postCount: posts.length,
      isEditting: null
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
