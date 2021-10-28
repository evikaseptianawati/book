<template>
<div class="book-table">
  <table class="table table-bordered">
  <thead class="thead-dark">
    <tr> 
      <th scope="col">ISBN</th>
      <th scope="col">Title</th>  
      <th scope="col">Author</th>
      <th scope="col">Publisher Name</th>
      <th scope="col">Publisher Year</th>
      <th scope="col">Genre</th>
      <th scope="col">Synopsis</th>
      <th scope="col">Status</th>
      <th scope="col">Action</th>
      
    </tr>
  </thead>
  <tbody> 
    <tr v-for="book in books" :key="book.id">
    <template v-if="bookId === book.id">
      <td>
        <label for="isbn" class="font-weight-bold">ISBN:</label>
        <div> 
          <input type="text" v-model="book.isbn" class="form-control" />
        </div>
      </td>
      <td>
        <label for="title" class="font-weight-bold">Title:</label>
        <div> 
          <input type="text" v-model="book.title" class="form-control" />
        </div>
      </td>
      <td>
        <label for="author" class="font-weight-bold">Author:</label>
        <div> 
          <input type="text" v-model="book.author" class="form-control"  />
        </div>
      </td>
      <td>
        <label for="publisher_name" class="font-weight-bold">Publisher Name:</label>
        <div> 
          <input type="text" v-model="book.publisher_name" class="form-control"  />
        </div>
      </td>
      <td>
        <label for="publisher_year" class="font-weight-bold">Publisher Year:</label>
        <div> 
          <input type="text" v-model="book.publisher_year" class="form-control"  />
        </div>
      </td>
      <td>
        <label for="genre" class="font-weight-bold">Genre:</label>
        <div> 
          <input type="text" v-model="book.genre" class="form-control"  />
        </div>
      </td>
      <td>
        <label for="synopsis" class="font-weight-bold">Synopsis:</label>
        <div> 
          <input type="text" v-model="book.synopsis" class="form-control"  />
        </div>
      </td>
      <td>
        <label for="status" class="font-weight-bold">Status:</label>
        <div> 
          <input type="text" v-model="book.status" class="form-control"  />
        </div>
      </td>

      <td> 
        <div class="mt-4">
        <button class="btn btn-success m-2" @click="saveEdit(book)">Save</button>
        <button class="btn btn-danger" @click="cancelEdit(book)" >Cancel</button>
        </div>
      </td>
    </template>
    <template v-else>
      <td>{{book.isbn}}</td>
      <td>{{book.title}}</td>
      <td>{{book.author}}</td>
      <td>{{book.publisher_name}}</td>
      <td>{{book.publisher_year}}</td>
      <td>{{book.genre}}</td>
      <td>{{book.synopsis}}</td>
      <td>{{book.status}}</td>
      <td>
        <div class="text-center">
         <button class="btn btn-primary mr-2" @click="editbook(book)">Edit</button>
         <button class="btn btn-danger" @click="deletebook(book.id)">Delete</button> 
        </div>
      </td>
    </template>
  </tr>
  </tbody>
</table>
</div>
</template>

<script>
 

  export default {
    name: 'book-table', 
    props: {
      books: Array,
    },
    data() {
      return {
          bookId: null,
        }
      },
      methods: {
        editbook(book) { 
          this.data = Object.assign({}, book)
          this.bookId = book.id 
          // console.log(this.data);
        },
        saveEdit(book) { 
          let id = this.data.id
          this.$emit('edit-book', id, book)  
          this.bookId = null
        },
        cancelEdit(book) { 
          Object.assign(book, this.data)
          this.bookId = null;
          // console.log(this.bookId);
        },
        deletebook(id){
          this.$emit('delete-book', id)  
        }
      }
  }
</script>

<style scoped> 
</style> 