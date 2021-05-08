<template>
  <div id="Effectifmodule">
    <h1>Effectif</h1>
    <listevoitures></listevoitures>
    <listejoueurs></listejoueurs>
  </div>
</template>

<script>
import axios from "axios";
import listevoitures from "./Listevoitures";
import listejoueurs from "./Listejoueurs";
export default {
  name: "effectif",
components: {listevoitures, 
listejoueurs}, 
  data() {
    return {
    };
  },
  methods: {
  },
};
</script>

<style>
#Effectifmodule {
  background-color: #7f7f7f;
  
}
</style>