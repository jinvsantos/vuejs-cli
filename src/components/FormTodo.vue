<template>
  <div>
    <p>
      <input placeholder="nome" type="text" name="author" class="form-control" v-model="name"/>
    </p>
    <p>
      <textarea placeholder="Comentario" name="message" class="form-control" v-model="message"></textarea>
    </p>
    <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        name: '',
        message: ''
      }
    },
    methods: {
      addComment() {
      if (this.message.trim() === '') {
        return
      }

      this.$emit('add-todo', {
        name: this.name,
        message: this.message,
      });
      
      this.name = ''
      this.message = ''
     }
  }
}
</script>