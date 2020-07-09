<template>
<div id="bookList">
  <Book v-for="book in books" :key="book.id" :book="book" />
</div>
</template>

<script>
import {eventBus} from "../main";
import Book from './Book.vue';

let nextBookId = 1

export default {
  components: {
    Book
  },
  data() {
    return {
      books: [{
          id: nextBookId++,
          title: 'Book 01',
          author: 'Author 01',
          pages: '422'
        },
        {
          id: nextBookId++,
          title: 'Book 02',
          author: 'Author 02',
          pages: '375'
        }
      ]
    }
  },
  created() {
    eventBus.$on('adding-book', (title, author, pages) => {
        this.books.push({
          id: nextBookId++,
          title: title,
          author: author,
          pages: pages
        })
      }),
    eventBus.$on('removing-book', (id) => {
      this.books = this.books.filter(book => {
        return book.id !== id
      })
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#bookList {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-gap: 4px;
  width: 100%;
}
</style>
