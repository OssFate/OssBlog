<template>
  <div class="ossblog">
    <h1>{{ titleMsg }}</h1>
    <h3>{{ message }}</h3>
    <h3>{{ snapVal }}</h3>
    <button @click="getData()">Get Data</button>
    <!-- <p>
      For a guide and recipes on how to configure / customize this project,<br>
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-typescript" target="_blank" rel="noopener">typescript</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a></li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul>-->
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import * as firebase from "firebase/app";

import "firebase/database";

const config = {
  apiKey: "AIzaSyD54K7VBHkU1tSAAymI1JPmnS7lvmmukEM",
  authDomain: "ossbio-d6647.firebaseapp.com",
  databaseURL: "https://ossbio-d6647.firebaseio.com"
};
firebase.initializeApp(config);

@Component
export default class OssBlog extends Vue {
  public message: string = "Hello World!";

  @Prop() private titleMsg!: string;

  private db: firebase.database.Database = firebase.database();
  private testRef: firebase.database.Reference = this.db.ref("posts");

  private snapVal = [];

  public async setData() {
    await this.testRef.set({
      name: "Oswald Mantilla",
      testing: "RealNames",
      array: ["one", "two", "three"]
    });
  }

  public async getData() {
    this.testRef.on("value", (a, b) => {
      //   console.log(a.val());
      this.snapVal = a.val();
      //   console.log(b);
    });
    // this.snapVal = snap.val();
  }

  private mounted() {
    this.getData();
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
</style>
