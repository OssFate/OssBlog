<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

:root {
  --color-primary-0: #2c3e50;
  --color-primary-1: #617487;
  --color-primary-2: #42586e;
  --color-primary-3: #1b3147;
  --color-primary-4: #0c2032;
  --color-secondary-1-0: #343256;
  --color-secondary-1-1: #6d6b91;
  --color-secondary-1-2: #4d4a76;
  --color-secondary-1-3: #23214c;
  --color-secondary-1-4: #121036;
  --color-secondary-2-0: #2a5344;
  --color-secondary-2-1: #618b7c;
  --color-secondary-2-2: #417160;
  --color-secondary-2-3: #194938;
  --color-secondary-2-4: #0a3425;
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
