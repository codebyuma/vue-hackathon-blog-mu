<template>
  <div class="hello">
    <h3>{{ thePost.title }}</h3>
    <p>{{ thePost.author }}</p>
    <p>{{ thePost.label }}</p>
    <button v-on:click="() => { remove(thePost.id); }">X</button>
  </div>
</template>

<script>
export default {
  name: 'Post',
  props: {'thePost': { title: String, author: String, label: String, id: Number },
  remove: Function}
}
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
