<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show" class="m-5">
      <b-form-group
        id="input-group-1"
        label="Your Name:"
        label-for="input-1"
        class="mb-3"
      >
        <b-form-input
          id="input-1"
          v-model="form.nombre"
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
          v-model="form.telefono"
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
          v-model="form.correo"
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
          v-model="form.fechaNacimiento"
          placeholder="Enter birth date"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Form",
  data() {
    return {
      form: {
        nombre: "",
        telefono: "",
        correo: null,
        fechaNacimiento: "",
      },
      show: true,
    };
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
        .post("https://examen.avirato.com/client/post", this.form, config)
        .then((result) => {
          this.$router.replace("/");
          console.log(result.data);
        });
    },
    onReset(event) {
      event.preventDefault();
      this.form.correo = "";
      this.form.nombre = "";
      this.form.telefono = null;
      this.form.fechaNacimiento = "";
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    },
  },
};
</script>
