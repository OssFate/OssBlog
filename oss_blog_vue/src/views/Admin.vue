<template>
  <div id="admin">
    <!-- <h1>This is an about page</h1> -->
    <Login/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Login from "@/components/Login.vue";

@Component({
  components: {
    Login
  }
})
export default class Admin extends Vue {}
</script>

<style>
#admin {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
