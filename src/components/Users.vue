<template>
  <div>
      <h3>List of Users from Rest API</h3>
      <table>
        <tr>
            <th>Id</th>
            <th>Name</th>
            <th>Email</th>
            <th>Phone</th>
        </tr>
        <tr v-for="(user,i) in users" :key="i">
            <td>{{user.id}}</td>
            <td>{{user.name}}</td>
            <td>{{user.email}}</td>
            <td>{{user.phone}}</td>
        </tr>
    </table>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Users from '../types/users';
import axios from 'axios';

export default defineComponent({
  name: 'App',
  components: {},
  data(){
    return{
      users: [] as Users[]
    }
  },
  created(){
      axios.get('http://localhost:5000/api/v1/users')
      .then(response => {
          this.users = response.data.data
          
      })
      .catch(error => {
          console.log(error.message);
          
      })
  }
});
</script>

<style scoped>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
