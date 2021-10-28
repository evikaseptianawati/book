<template>
  <div class="book-form">
    <form @submit.prevent="submit">
      <div class="form-group">
        <label for="isbn">ISBN</label>
        <input type="text" v-model="book.isbn" class="form-control" placeholder="ISBN">
      </div>
      <div class="form-group">
        <label for="title">Title</label>
        <input type="text" v-model="book.title" class="form-control" placeholder="Title">
      </div>
      <div class="form-group">
        <label for="author">Author</label>
        <textarea type="text" v-model="book.author" class="form-control" 
          placeholder="Author"> </textarea>
      </div>
       <div class="form-group">
        <label for="publisher_name">Publisher Name</label>
        <textarea type="text" v-model="book.publisher_name" class="form-control" 
          placeholder="Publisher Name"> </textarea>
      </div>
       <div class="form-group">
        <label for="publisher_year">Publisher Year</label>
        <textarea type="text" v-model="book.apublisher_year" class="form-control" 
          placeholder="Publisher Year"> </textarea>
      </div>
       <div class="form-group">
        <label for="genre">Genre</label>
        <textarea type="text" v-model="book.genre" class="form-control" 
          placeholder="Genre"> </textarea>
      </div>
       <div class="form-group">
        <label for="synopsis">Synopsis</label>
        <textarea type="text" v-model="book.synopsis" class="form-control" 
          placeholder="Synopsis"> </textarea>
      </div>
       <div class="form-group">
        <label for="status">Status</label>
        <textarea type="text" v-model="book.status" class="form-control" 
          placeholder="Status"> </textarea>
      </div>
      <button type="submit" class="btn btn-primary mr-2">Submit</button>
      <button class="btn btn-danger" type="button" data-toggle="collapse" data-target="#collapseExample">
        Cancel
        </button>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'book-form', 
    data(){
      return {
        book: {
          isbn: '',
          title: '',
          author: '',
          publisher_name: '',
          publisher_year: '',
          genre: '',
          synopsis: '',
          status: '',
        }
      }
    },
    methods: {
      submit() {
        this.$emit('add-book', this.book)
        this.book = {
          isbn: '',
          title: '',
          author: '',
          publisher_name: '',
          publisher_year: '',
          genre: '',
          synopsis: '',
          status: '',
        }
      },
    },
  }
</script>