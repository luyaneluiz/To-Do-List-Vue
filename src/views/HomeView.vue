<template>
  <div class="home">
    <div class="container">
      <FormTask />
    </div>
  </div>
</template>

<script>
import FormTask from "../components/FormTask.vue";

export default {
  name: "HomeView",
  components: {
    FormTask,
  },
};
</script>

<style>
.home {
  background: linear-gradient(rgb(79, 90, 98), rgb(196, 196, 196));
  height: 100vh;
  padding: 50px 0;
}

.container {
  border: 2px solid #ccc;
  width: 85%;
  padding: 20px;
  margin: auto;
  border-radius: 5px;
}

@media (min-width: 730px) {
  .container {
    width: 60%;
  }
}

@media (min-width: 950px) {
  .container {
    width: 40%;
  }
}
</style>
