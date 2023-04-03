<template>
  <div class="container">
    <h2>Member List</h2>
   <div>
      <table class="table table-primary">
        <thead>
          <tr>
            <th scope="col">id</th>
            <th scope="col">name</th>
            <th scope="col">job</th>
            <th scope="col">home</th>
          </tr>
        </thead>
        <tbody :value="member.id" :key="member.id" v-for="member in members">
          <tr>
            <th scope="row">{{member.id}}</th>
            <td>{{member.name}}</td>
            <td>{{member.job}}</td>
            <td>{{member.home}}</td>
          </tr>
        </tbody>
      </table>
    </div>     
  </div>
</template>

<script>
import { ref } from 'vue';
import axios from "axios";

export default {
  name: 'App',
  setup(){
    axios.defaults.baseURL = 'http://localhost:8000';
    axios.defaults.headers.post['Content-Type'] ='application/json;charset=utf-8';
    axios.defaults.headers.post['Access-Control-Allow-Origin'] = '*';

    const members = ref([]);

    const getMembers = async () => {
      console.log("ok!!!!!!!!!!!!");
      try{
        const res = await axios.get('/members');               
        members.value = res.data;
        console.log(res.data);
      }catch(err){
        console.log(err);
      }
    }

    getMembers();

    return {
      members,
      getMembers,
    };
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
