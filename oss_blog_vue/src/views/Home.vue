<template>
  <div id="home">
    <OssBlog titleMsg="OssBlog" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import OssBlog from "@/components/OssBlog.vue";

@Component({
  components: {
    OssBlog
  }
})
export default class Home extends Vue {}
</script>

<style>
#home {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
