<template>
  <div id="app">
    <h1>Contact List Application</h1>
    <hr />
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.list {
  display: flex;
  border: 1px solid #000;
  justify-content: center;
  flex-direction: column;
}
</style>
