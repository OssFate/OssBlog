<template>
  <div id="login">
    <div class="login">
      <div class="middle">
        <div class="inner">
          <h1>Creator HUB</h1>
          <input v-model="user" placeholder="User">
          <br>
          <input v-model="pwd" type="password" placeholder="Password" @keyup.enter="FireLogin">
          <br>
          <button @click="FireLogin()">
            <b>Login</b>
          </button>
          <!-- <p>User is: {{ user }} and pass: {{ password }}</p> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import * as firebase from "firebase/app";

import "firebase/firebase-auth";

// firebase.initializeApp(config);

@Component
export default class Login extends Vue {
  public message: string = "Hello, World!";

  private auth: firebase.auth.Auth;

  private user: string = "";
  private pwd: string = "";

  constructor() {
    super();

    this.auth = firebase.auth();
  }

  private FireLogin() {
    alert(`login in ${this.user} with pwd ${this.pwd}`);
    // console.log("trying login");
    this.auth
      .signInWithEmailAndPassword(this.user, this.pwd)
      .then((data: any) => {
        console.log(data);
      })
      .catch((error: any) => {
        console.log(error);
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.login {
  display: table;
  margin: 0 auto;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.login .middle {
  display: table-cell;
  vertical-align: middle;
}

.login .middle .inner {
  margin-left: auto;
  margin-right: auto;
  padding-bottom: 60px;
}

input {
  text-align: center;
  border: 2px solid var(--color-primary-0);
  border-radius: 4px;
  margin-bottom: 10px;
  padding-block-start: 4px;
  padding-block-end: 4px;
  padding-inline-start: 40px;
  padding-inline-end: 40px;
  outline: none;
}

input:focus {
  border: 2px solid var(--color-secondary-1-1, black);
}

input::placeholder {
  color: var(--color-primary-2);
}

button {
  color: white;
  border: 2px solid var(--color-primary-1);
  border-radius: 4px;
  background-color: var(--color-primary-4);
  padding-block-start: 4px;
  padding-block-end: 4px;
  padding-inline-start: 20px;
  padding-inline-end: 20px;
  outline: none;
}

button:focus {
  border: 2px solid var(--color-secondary-1-2);
  background-color: var(--color-secondary-1-1);
}
</style>
