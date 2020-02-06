<template>
  <div id="app">
    <h1 @click="show=!show">TODO</h1>
    <Card :show="show"/>
  </div>
</template>

<script>

import Card from "./Card";

export default {
  name: 'app',
  components: { Card },
  data() {
    return {
      show: true,
    }
  },
  methods: {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 1280px;
  margin: 0 auto;
}

p {
  margin: 0;
}
.form {
  width: 400px;
  margin-left: auto;
}
.form p {
  margin-bottom: 10px;
}

.form button {
  width: 100%;
  height: 30px;
  line-height: 30px;
}
input {
  border: 1px solid #333;
  width: 100%;
  height: 30px;
  line-height: 30px;
  padding: 0 8px;
  box-sizing: border-box;
}


.icons p {
  margin-right: 5px;
}
</style>
