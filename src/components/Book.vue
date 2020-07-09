<template>
  <div class="bookCard">
    <div class="bookInfo">
      <div class="bookTitle">{{ book.title }}</div>
      <div class="bookAuthor">By {{ book.author }}</div>
      <div class="bookPages">{{ book.pages }} pages</div>
    </div>
    <div class="bookRead">
      <input type="checkbox" class="bookReadCheck" checked="true">
      <label class="bookReadLabel">Read this</label>
    </div>
    <button class="bookDelete" @click="removeBookFromLibrary(book.id)"></button>
  </div>
</template>

<script>
import {eventBus} from "../main";

export default {
  props: {
     book: {
       type: Object,
       required: true
     }
   },
   methods: {
     removeBookFromLibrary(id) {
       eventBus.$emit('removing-book', id);
     }
   }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.bookCard {
    background-color: white;
    height: 120px;
    padding: 8px;
    box-shadow: 0 1px 6px 0 rgba(32,33,36,0.28);
    display: grid;
    grid-template-columns: 75% 25%;
    grid-template-rows: 75% 25%;
}

.bookTitle {
    grid-column: 1 / span 2;
    margin-bottom: 4px;
}

.bookAuthor, .bookPages {
    font-size: 12px;
    margin-bottom: 2px;
}

.bookAuthor, .bookPages, .bookRead {
    grid-column: 1 / span 1;
}

.bookReadCheck {
    margin: 10px 0;
}

.bookReadLabel {
    font-size: 14px;
    margin-left: 4px;
}

.bookDelete {
    background-color: transparent;
    background-image: url(../assets/delete.svg);
    border: none;
    width: 100%;
    height: 100%;
    background-size: 20px;
    background-repeat: no-repeat;
    padding: unset;
    background-position: center;
    cursor: pointer;
}

</style>
