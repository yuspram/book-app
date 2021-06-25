<template>
  <div class="hello">
    <h1>Test component</h1>
    <div class="container">
      <div v-for="book in books" :key="book.id" class="bookList">
        <img :src="book.volumeInfo.imageLinks.thumbnail" alt="">
        <p>{{ book.volumeInfo.title }}</p>
        <p>{{ book.volumeInfo.authors.toString() }}</p>
        <div>
          {{ book.volumeInfo.ratingsCount }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',
  data() {
    return {
        books: "hallo"
    };
  },
  mounted() {
    axios
    .get(' https://www.googleapis.com/books/v1/volumes?q=harry')
    .then(response => {
      // console.log(response.data.items.map( item =>  item[0].title))
      return this.books = response.data.items
    })
  },
}
</script>

<style scoped>
.container {
  display: flex;
}

.bookList {
  margin: 5px;
  padding: 5px;
  width: 200px;
  border: 2px solid black;
}
</style>