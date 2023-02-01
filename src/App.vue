<template>
  <div id="app">
   <main-page></main-page>
   <table class="table mb-0">
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Address</th>
            <th scope="col">OperatingSystem</th>
            <th scope="col">Language</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="postss in posts" v-bind:key="postss.id" class="fw-normal">
            <th>
              <span>{{ postss.name }}</span>
            </th>
            <td class="align-middle">
              <span>{{ postss.address }}</span>
            </td>
            <td class="align-middle" >
              <p v-bind:key="data" v-for="data in postss.operatingSystem">{{ data }}</p>
            </td>
            <td class="align-middle">
              <span>{{ postss.value }}</span>
            </td>
            <td class="align-middle">
              <span>{{ postss.language }}</span>
            </td>
            <td class="align-middle">
              <button  class="btn btn-warning rounded-2" @click="showModal(task)">edit</button>
              <button v-on:click="removeItem(postss.id)" class="btn btn-warning rounded-2">delete</button>
              
            </td>

          </tr>

        </tbody>
      </table>
  </div>
</template>

<script>
import MainPage from './components/MainPage.vue';
import axios from 'axios'
import 'bootstrap/dist/css/bootstrap.min.css'
export default {
  name: 'App',

  components: {
   'main-page':MainPage
  },
  props:{
    postss:Array

  },

  data(){
    return{
   //   postss:[],
      posts:[]
    }
  },
  async created() {
    try {
      const res = await axios.get(`http://localhost:3000/postss`);
      this.posts = res.data;
      
    } catch (error) {
      console.log(error);
    }},
  methods:{
   
    removeItem(id) {
      axios.delete(`http://localhost:3000/postss/${id}`);
      this.posts = this.posts.filter((postss) => postss.id !== id);
   
    },
  }
}
</script>

<style>

</style>
