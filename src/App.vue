<template>
  <div id="app">
    <img class="logobatd" src="./assets/batd.png" />
    <h1>{{ msgbienvenue }}</h1>
      <div>
      <router-link to="/effectif">Effectif</router-link>
      <router-link to="/matchs">Matchs</router-link>
      <router-view></router-view>
      </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      msgbienvenue: "The Cure"
    };
  }
};
</script >

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}
li {
  list-style-type: none;
}
a {
  color: rgb(10, 76, 85);
}
.logobatd {
  height: 300px;
  width: 300px;
}
</style>