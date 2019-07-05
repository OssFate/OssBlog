<template>
  <div id="notfound">
    <h1>You are in the wrong place m8!</h1>
    <!-- Add Button for go Home -->
    <router-link to="/">
      <button>Go Home</button>
    </router-link>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

export default class NotFound extends Vue {}
</script>