<template>
  <div id="Modulejoueurs">
    <h2>Liste des Joueurs</h2>
    <div class="listejoueurs">
    <li v-for="(joueur) in listejoueurs" :key="joueur.id">
      <Joueur v-bind:joueur="joueur" @event_updatejoueur="UpdateJ" @event_deletejoueur="deletejoueur"></Joueur>
    </li>
    </div>
    <input type="text" v-model="joueur.firstname" />
    <input type="text" v-model="joueur.lastname" />
    <input type="text" v-model="joueur.classement" />
    <button v-on:click="addjoueur">Ajouter un joueur</button>
  </div>
</template>

<script>
import axios from "axios";
import Joueur from "./Joueur";
export default {
  name: "listejoueurs",
  components: { Joueur },
  data() {
    return {
      joueur: {
        id: 0,
        firstname: "Prénom",
        lastname: "Nom",
        classement: "classement"
      },
      listejoueurs: [],
      uri: "http://localhost:3000/api/effectifj/"
    };
  },

  methods: {
    getlisteeffectifj: function() {
      axios.get(this.uri).then(response => { 
        this.listejoueurs = response.data.listejoueurs;
      });
    },
    addjoueur: function() {
      axios.post(this.uri, this.joueur).then(response => { 
        this.getlisteeffectifj();
      });
    },
    UpdateJ: function(joueur) {
      axios.put(this.uri + joueur.id, joueur).then(response => {
        console.log(reponse.data);
      });
    },
  
  deletejoueur: function(joueur) {
      axios.delete(this.uri + joueur.id).then(response => {
        console.log(response.data);
        this.getlisteeffectifj();
      });
    },
  },
  mounted() {
    this.getlisteeffectifj();
  }
};
</script>


<style>
#Modulejoueurs {
  background-color: #7f7f7f;
}
.listejoueur {
  display : flex;
  justify-content: space-evenly;
  flex-wrap : wrap;
  
}
</style>