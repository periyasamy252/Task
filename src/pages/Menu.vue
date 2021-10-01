<template>
  
  <div class="q-pa-md">
<q-layout view="lHh Lpr lff"  class="shadow-2 rounded-borders">
    <q-header elevated class="bg-blue-5 text-white" height-hint="64">
        <q-toolbar>
            <q-btn flat dense round @click="leftDrawerOpen!=leftDrawerOpen" icon="menu"/>
            <q-toolbar-title>Menu</q-toolbar-title>
        </q-toolbar>
    </q-header>
  <h6>Data</h6>
  <ul v-for="post in todos" v-bind:key="todos.id">
    <li>{{post.title}}</li>
    <p>{{post.body}}</p>
  </ul>
</q-layout>
  </div>
</template>

<script>
import axios from "axios";
// Vue.prototype.$http = axios;
export default {
  data(){
    return{
    todos: [],
    data:{},
    column:[
      { name: 'User ID', align : 'left', label:'User Id', field:'userId'},
      { name: 'ID', align : 'left', label:'Id', field:'id'},
      { name: 'Title', align : 'left', label:'Title', field:'title'},
      { name: 'Body', align : 'left', label:'Body', field:'body'},
    ],

  }},
  created() {
    // axios.get("https://jsonplaceholder.typicode.com/posts").then((result) => {
    //   this.todos = result.data;
    //   this.data = result.data
    this.getData()
      console.log('data------->',this.todos)
    // })
  },
   methods: {
    async getData() {
      try {
        console.log('called')
        const response = await fetch("http://jsonplaceholder.typicode.com/posts");
        // JSON responses are automatically parsed.
        this.todos = await response.json();;
        console.log('todos------>',this.todos)
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped lang="scss">
</style>

<style scoped lang="scss">
</style>
