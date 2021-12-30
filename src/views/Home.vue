<template>
  <div class="home">
    <Search />
    <Users />
  </div>
</template>

<script>
// @ is an alias to /src
import Users from "@/components/Users.vue";
import Search from "@/components/Search.vue";

export default {
  name: "Home",
  components: {
    Users,
    Search,
  },
};
</script>
