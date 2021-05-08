<template>
  <div id="Matchmodule">
    <h1>Matchs</h1>
    <listematchs></listematchs>
    
    
  </div>
</template>
<script>
import axios from "axios";
import listematchs from "./ListeMatchs";
export default {
  name: "matchs",
components: {listematchs}, 
  data() {
    return {
    };
  },
  methods: {
  },
};
</script>


<style>
#Matchmodule {
  background-color: #7f7f7f;
}
</style>