<template>
  <div class="ossblog">
    <h1>{{ titleMsg }}</h1>
    <h3>{{ message }}</h3>
    <h3>{{ snapVal }}</h3>
    <button @click="setData()">Set Data</button>
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
    await this.testRef.push({
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
