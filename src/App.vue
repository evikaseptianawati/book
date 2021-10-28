<template>
  <div id="app">
    <div class="container">
      <h1 class="mb-4">Book List</h1>
      <hr>
      <p> 
        <button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
        Add Book
        </button>
      </p>

      <book-table 
        v-bind:books='books' 
        @edit-book="editbook"
        @delete-book="deletebook"
      />

      <div class="collapse" id="collapseExample">
        <div class="card card-body">
          <h2>Add Book</h2>
          <hr>

          <!-- <book-form @add-book="addbook"/> -->
          <book-form @add-book="addbook"/>

        </div>
      </div>
    </div>
  </div>
</template>


<script>
import bookTable from '@/components/bookTable.vue'
import bookForm from '@/components/bookForm.vue'

export default {
  name: 'App',
  components: {
    bookTable,
    bookForm, 
  },
  data() {
    return {
      books: [
        {
          id: 1,
          isbn: '12345678',
          title: 'Book A',
          author: 'Author A',
          publisher_name: 'Publisher A',
          publisher_year: '2020',
          genre: 'Action',
          synopsis: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
          status: 'Available',
        },
        {
          id: 2,
          isbn: '123455677',
          title: 'Book B',
          author: 'Author B',
          publisher_name: 'Publisher B',
          publisher_year: '2020',
          genre: 'Thriller',
          synopsis: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
          status: 'Available',
        },
        {
          id: 3,
          isbn: '1234556779',
          title: 'Book C',
          author: 'Author C',
          publisher_name: 'Publisher C',
          publisher_year: '2021',
          genre: 'Action',
          synopsis: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
          status: 'Available',
        },
      ],
    }
  },
  methods: {
    addbook(book) {
      this.books.push(book);
    },
    editbook(id, data) {
      this.books = this.books.map(function (book) { 
        return book.id === id ? data : book;
      });
    },
    deletebook(id) {
      this.books = this.books.filter(function (book) { 
        return book.id !== id;
      });
    }
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
