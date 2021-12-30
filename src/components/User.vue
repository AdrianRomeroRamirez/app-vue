<template>
  <div>
    <b-form @submit="onSubmit" v-if="show" class="m-5">
      <b-form-group
        id="input-group-1"
        label="Your Name:"
        label-for="input-1"
        class="mb-3"
      >
        <b-form-input
          id="input-1"
          v-model="user.nombre"
          placeholder="Enter name"
          required
          value="qq"
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-2"
        label="Your phone number:"
        label-for="input-2"
        class="mb-3"
      >
        <b-form-input
          id="input-2"
          v-model="user.telefono"
          type="number"
          placeholder="Enter phone number"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-3"
        label="Email address:"
        label-for="input-3"
        class="mb-3"
      >
        <b-form-input
          id="input-3"
          v-model="user.correo"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-4"
        label="Your birth date:"
        label-for="input-4"
        class="mb-3"
      >
        <b-form-input
          id="input-4"
          v-model="user.fechaNacimiento"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Update</b-button>
      <b-button v-on:click="borrar" variant="danger">Delete</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "User",
  data() {
    return {
      user: {},
      id: this.$route.params.id,
      show: true,
    };
  },

  created: function () {
    const config = {
      headers: {
        Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjUwLCJpYXQiOjE2NDA4NTgwNzIsImV4cCI6MTY0MDg2NTI3Mn0.Y3nEeI1bKOdUGuIxc7AYYlNQ8mXzks0cZ6pJUDabFNA`,
      },
    };
    axios
      .get("https://examen.avirato.com/client/get/one/" + this.id, config)
      .then((res) => {
        this.user = res.data;
      });
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      const config = {
        headers: {
          Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjUwLCJpYXQiOjE2NDA4NTgwNzIsImV4cCI6MTY0MDg2NTI3Mn0.Y3nEeI1bKOdUGuIxc7AYYlNQ8mXzks0cZ6pJUDabFNA`,
        },
      };
      axios
        .put("https://examen.avirato.com/client/put", this.user, config)
        .then((result) => {
          this.$router.replace("/");
          console.log(result.data);
        });
    },
    borrar() {
      const config = {
        headers: {
          Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjUwLCJpYXQiOjE2NDA4NTgwNzIsImV4cCI6MTY0MDg2NTI3Mn0.Y3nEeI1bKOdUGuIxc7AYYlNQ8mXzks0cZ6pJUDabFNA`,
        },
      };
      axios
        .delete("https://examen.avirato.com/client/delete/" + this.id, config)
        .then((result) => {
          this.$router.replace("/");
          console.log(result.data);
        });
    },
  },
};
</script>
