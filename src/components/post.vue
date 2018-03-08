<template>
  <div class="hello">
    <span v-if="isEditting !== thePost.id">
      <h3>{{ thePost.title }}</h3>
      <p>{{ thePost.author }}</p>
      <p>{{ thePost.label }}</p>
      <button @click="() => { edit(thePost.id); toggle(thePost.id); }">edit</button>
      <button @click="() => { remove(thePost.id); }">X</button>
    </span>
    <span v-else>
      <AddPost :submit="edit" :newPost="thePost"/>
    </span>
  </div>
</template>

<script>
import AddPost from "./addPost.vue";

export default {
  name: "Post",
  components: {
    AddPost
  },
  props: {
    thePost: { title: String, author: String, label: String, id: Number },
    remove: Function,
    edit: Function,
    toggle: Function,
    isEditting: Number
  }
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
