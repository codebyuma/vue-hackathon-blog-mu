<template>
    <div>
    <h2>Add a new post:</h2>
    <form @submit.prevent="() => { submit(newPost); clearForm();}">
        Title: <input v-model="newPost.title" />  
        Author: <input v-model="newPost.author" /> 
        Label: <input v-model="newPost.label" />
        <button>Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'AddPost',
  props: {
      submit: Function
  },
  methods: {
      clearForm() {
          this.newPost = {}
      }
  },
  data: () => ({
    newPost: {
    title: '',
    author: '',
    label: '',
  }})
}
</script>