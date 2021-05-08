<template>
  <div id="modulevoitures">
    <h2>Liste des Voitures</h2>
    <div class="listevoitures">
    <li v-for="(voiture) in listevoitures" :key="voiture.id">
      <Voiture v-bind:voiture="voiture" @event_updatevoiture="UpdateV" @event_deletevoiture="deletevoiture"></Voiture>
    </li>
    </div>
    <input type="text" v-model="voiture.name" />
    <button v-on:click="addvoiture">Ajouter une Voiture</button>
  </div>
</template>

<script>
import axios from "axios";
import Voiture from "./Voiture";
export default {
  name: "listevoitures",
  components: { Voiture },
  data() {
    return {
      voiture: {
        id: 0,
        name: "Nom"
      },
      listevoitures: [],
      uri: "http://localhost:3000/api/effectif/"
    };
  },
  methods: {
    getlisteeffectif: function() {
      axios.get(this.uri).then(response => {
        this.listevoitures = response.data.listevoitures;
      });
    },
    addvoiture: function() {
      axios.post(this.uri, this.voiture).then(response => {
        console.log(response.data);
        this.getlisteeffectif();
      });
    },
    UpdateV: function(voiture) {
      axios.put(this.uri + voiture.id, voiture).then(response => {
        console.log(reponse.data);
      });
    },
    deletevoiture: function(voiture) {
      axios.delete(this.uri + voiture.id).then(response => {
        console.log(response.data);
        this.getlisteeffectif();
      });
    }
  },
  mounted() {
    this.getlisteeffectif();
  }
};
</script>


<style>
#modulevoitures {
  background-color: #7f7f7f;
}
.listevoitures {
  display : flex;
  justify-content: space-evenly;
  flex-wrap : wrap;
}
</style>