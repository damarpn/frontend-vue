<template>
  <Navbar />
  <router-view :bookList="booksData" @store="storeData" @update="updateData" @delete="deleteData" />
</template>

<script>
import Navbar from './components/Navbar.vue';

export default {
  name: 'App',
  components: {
    Navbar
  },
  methods: {
    storeData(bookCreated) {
      console.log(bookCreated);
      alert("Data berhasil ditambahkan!");
      this.booksData.push(bookCreated);
    },
    updateData(bookChanged, bookIndex) {
      console.log(bookChanged, bookIndex);     
      alert("Data berhasil diperbarui!");
      this.booksData[bookIndex] = bookChanged;
    },
    deleteData(book, index) {
      console.log(book);
      console.log(index);
      //this.$delete(this.booksData, 1);
      this.booksData.splice(index,1);
      alert("Data berhasil dihapus!");
    },
  },
  data() {
    return {
      booksData:[
        {
          _id: 1,
          judul: "Laskar Pelangi",
          pengarang: "Andrea Hirata",
          harga: 80000,
          stok: 7
        },
        {
          _id: 2,
          judul: "Bumi",
          pengarang: "Tere Liye",
          harga: 85000,
          stok: 5
        }
      ],
    };
  },
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
