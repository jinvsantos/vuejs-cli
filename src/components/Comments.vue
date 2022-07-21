<template>
  <div class="container">
    <h1>Comentarios</h1>
    <hr />
    <FormTodo v-on:add-todo = "addComment"></FormTodo>
    <div class="list-group">
    <div class="list-group-item" v-for="(comment, index) in Allcomments">
        <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
        <p>{{ comment.message }}</p>
        <div>
        <a href="#" title="Excluir" v-on:click="removeComment(index)">Excluir</a>
        </div>
    </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormTodo from './FormTodo';
export default {
  components: {
    FormTodo
  },
  data() {
    return {
      comments: []
    }
  },
  methods: {
    addComment(comment){
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1)
    }
  },
  computed: {
    Allcomments() {
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === '' ? 'Anônimo' : comment.name
      }))
    }
  }
}
</script>
