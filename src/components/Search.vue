<template>
  <div>
    <b-form @submit="onSubmit" v-if="show" class="m-5">
      <b-form-group
        id="input-group-1"
        label="Search:"
        label-for="input-1"
        class="mb-3"
      >
        <b-form-input
          id="input-1"
          v-model="search"
          placeholder="Search"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Search",
  data() {
    return {
      form: {
        search: "",
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
        .get(
          "https://examen.avirato.com/client/get/search?search=" +
            this.form.search,
          config
        )
        .then((result) => {
          alert(JSON.stringify(this.form));
          console.log(result.data);
        });
    },
  },
};
</script>
