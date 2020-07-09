<template>
<div>
  <div class="modal is-active">
    <div class="modal-background"></div>
    <div class="modal-card">
      <div class="modal-card-head">
        <p class="modal-card-title">Add book</p>
      </div>
      <section class="modal-card-body">
        <form id="new-book-form">
          <label for="title">Book title:</label>
          <input type="text" id="title" name="title" v-model="title">
          <label for="Author">Author:</label>
          <input type="text" id="author" name="author" v-model="author">
          <label for="pages"># of pages:</label>
          <input type="text" id="pages" name="pages" v-model="pages">
          <!-- <label for="read">I've read this book:</label>
          <div>
            <input type="radio" class="read-radio" id="have-read" name="read" checked="checked">
            <label for="have-read" class="read-label">Yes</label>
            <input type="radio" class="read-radio" id="have-not-read" name="read">
            <label for="have-not-read" class="read-label">No</label>
          </div>  -->
        </form>
      </section>
      <footer class="modal-card-foot">
        <button class="button is-success" @click="addBookToLibrary(title, author, pages)">Add book</button>
        <button class="button" @click="hideBookModal">Cancel</button>
      </footer>
    </div>
  </div>
</div>
</template>

<script>
import {eventBus} from "../main";

export default {
  data() {
    return {
      title: '',
      author: '',
      pages: ''
    }
  },
  methods: {
    hideBookModal() {
      this.$emit('hiding-modal');
    },
    addBookToLibrary(title, author, pages) {
      eventBus.$emit('adding-book', title, author, pages);
      this.$emit('hiding-modal');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import 'https://cdnjs.cloudflare.com/ajax/libs/bulma/0.9.0/css/bulma.css';

#new-book-form {
    display: inline-grid;
    width: 100%;
    margin-bottom: 4px;
}

input {
  margin-bottom: 16px;
}

.read-radio {
  margin-right: 4px;
}

.read-label {
  margin-right: 8px;
}


</style>
