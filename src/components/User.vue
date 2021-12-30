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
          v-model="form.name"
          placeholder="Enter name"
          required
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
          v-model="form.phone"
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
          v-model="form.email"
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
          v-model="form.birth"
          placeholder="Enter name"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Update</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "User",
  data() {
    return {
      user: null,
      id: this.$route.params.id,
      form: {
        name: "",
        email: "",
        phone: null,
        birth: "",
      },
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
      alert(JSON.stringify(this.form));
    },
  },
};
</script>
