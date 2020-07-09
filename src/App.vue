<template>
  <div id="App">
    <header>
      <h1>My library</h1>
      <button id="create-new" @click="showBookModal = true">Add book</button>
    </header>
    <BookList />
    <AddBookModal v-if="showBookModal" @hiding-modal="showBookModal = false" @adding-book="showBookModal = false"></AddBookModal>
  </div>
</template>

<script>
import BookList from './components/BookList.vue'
import AddBookModal from './components/AddBookModal.vue'

export default {
  name: 'App',
  components: {
    BookList, AddBookModal
  },
  data() {
    return {
      showBookModal: false
    }
  }
}
</script>

<style>

body {
    font-family: 'Helvetica', sans-serif;
    margin: 16px;
}

header {
    margin: 16px 0 16px 0;
}

h1 {
    font-size: 28px;
    display: inline;
}

#create-new {
    float: right;
    height: 32px;
    border: 1px solid #dfe1e5;
    border-radius: 4px;
    font-size: 16px;
    padding: 8px;
    cursor: pointer;
}

</style>
