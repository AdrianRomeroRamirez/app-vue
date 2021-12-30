<template>
  <div class="container">
    <h3>Users:</h3>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Name</th>
          <th scope="col">Phone</th>
          <th scope="col">Email</th>
          <th scope="col">Birth date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" v-bind:key="user.id">
          <th scope="row">{{ user.id }}</th>
          <td>{{ user.nombre }}</td>
          <td>{{ user.telefono }}</td>
          <td>{{ user.correo }}</td>
          <td>{{ user.fechaNacimiento }}</td>
          <router-link :to="'/user/' + user.id">Go</router-link>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Users",
  data() {
    return {
      users: null,
    };
  },
  created: function () {
    const config = {
      headers: {
        Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjUwLCJpYXQiOjE2NDA4NTgwNzIsImV4cCI6MTY0MDg2NTI3Mn0.Y3nEeI1bKOdUGuIxc7AYYlNQ8mXzks0cZ6pJUDabFNA`,
      },
    };
    axios.get("https://examen.avirato.com/client/get", config).then((res) => {
      this.users = res.data;
    });
  },
};
</script>
