<template>
  <div id="Modulejoueurs">
    <h2>Liste des Joueurs</h2>
    <div class="listejoueurs"> 
      <!-- afficher du contenu -->
    <li v-for="(joueur) in listejoueurs" :key="joueur.id">
      <!-- on récupère joueur du v-for ci-dessus et est lié au props dans joueur.vue + ajout d'evenements 2x@ -->
      <Joueur v-bind:joueur="joueur" @event_updatejoueur="UpdateJ" @event_deletejoueur="deletejoueur"></Joueur>
    </li>
    <!-- ajouter un joueur, binding entre le model et mon input -->
    </div>
    <input type="text" v-model="joueur.firstname" />
    <input type="text" v-model="joueur.lastname" />
    <input type="text" v-model="joueur.classement" />
     <!-- renvoie vers une methode pour ajouter à l'API, on addjoueur dans les methodes-->
    <button v-on:click="addjoueur">Ajouter un joueur</button>
  </div>
</template>

<script>
//appeler l'uri avec axios
import axios from "axios";
import Joueur from "./Joueur";
export default {
  name: "listejoueurs",
  components: { Joueur },
  data() {
    return {
      //ajouter un joueur
      joueur: {
        id: 0,
        firstname: "Prénom",
        lastname: "Nom",
        classement: "classement"
      },
      //tableau
      listejoueurs: [],
      uri: "http://localhost:3000/api/effectifj/"
    };
  },

  methods: {
    getlisteeffectifj: function() {
      axios.get(this.uri).then(response => { 
        this.listejoueurs = response.data;
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