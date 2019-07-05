<template>
  <div id="admin">
    <div v-if="loading" class="loading" />
    <div v-else>
      <Login v-on:logged="UserLoggedOn" v-if="login" />
      <p v-else>{{ msg }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import * as firebase from "firebase/app";
import Login from "@/components/Login.vue";

@Component({
  components: {
    Login
  }
})
export default class Admin extends Vue {
  private loading: boolean = true;
  private login: boolean = true;
  private msg: any = "";

  private mounted() {
    firebase.auth().onAuthStateChanged((user: any) => {
      if (user !== null) {
        this.login = false;
        this.msg = JSON.stringify(user);
      } else {
        this.login = true;
      }

      this.loading = false;
    });
  }

  // Recieve the onLogin signal, and change views with that
  private UserLoggedOn(message: any) {
    this.msg = JSON.stringify(message);
  }

  // Send to new Component which goes to control new posts
}
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

.loading {
  background-color: white;
}
</style>
