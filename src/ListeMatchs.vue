<template>
  <div id="Modulematchs">
    <h2>Liste des Matchs</h2>
    
    <li v-for="(match) in listematchs" :key="match.id">
      <Match v-bind:match="match" @event_updatematch="UpdateM" @event_deletematch="deletematch"></Match>
    </li>

    <fieldset class="fieldsetadd">
      <legend><strong>Ajouter un Match :</strong> </legend> 
        <div class="infomatchadd">
      Titre: <input type="text" v-model="match.titre" /> <br>
      Date: <input type="date" v-model="match.date" /> <br>
      Heure: <input type="time" v-model="match.heure" /> <br>
      Adresse: <input type="text" v-model="match.adresse" /> <br>
      Voiture du jour: <input type="text" v-model="match.matchvoiture" /> <br>
        Joueur1: <input size='12' type="text" v-model="match.joueur1" />
        Joueur2: <input size='12' type="text" v-model="match.joueur2" />
        Joueur3: <input size='12' type="text" v-model="match.joueur3" />
        Joueur4: <input size='12' type="text" v-model="match.joueur4" />
        Joueur5: <input size='12' type="text" v-model="match.joueur5" />
        Joueur6: <input size='12' type="text" v-model="match.joueur6" />
        </div>
      <button class="boutonadd" v-on:click="addmatch">Ajouter un Match</button>
    </fieldset>
  </div>
</template>

<script>
import axios from "axios";
import Match from "./Match";
export default {
  name: "listematchs",
  components: { Match },
  data() {
    return {
      match: {
        id: 0,
        titre: "titre",
        date: "date",
        heure: "00:00",
        adresse: "adresse",
        matchvoiture: "matchvoiture",
        joueur1 : "joueur1",
        joueur2 : "joueur2",
        joueur3 : "joueur3",
        joueur4 : "joueur4",
        joueur5 : "joueur5",
        joueur6 : "joueur6",
      },
      listematchs: [],
      uri: "http://localhost:3000/api/matchs/"
    };
  },
  methods: {
    getlistematch: function() {
      axios.get(this.uri).then(response => {
        this.listematchs = response.data.listematchs;
      });
    },
    addmatch: function() {
      axios.post(this.uri, this.match).then(response => {
        console.log(response.data);
        this.getlistematch();
      });
    },
    UpdateM: function(match) {
      axios.put(this.uri + match.id, match).then(response => {
        console.log(reponse.data);
      });
    },
    deletematch: function(match) {
      axios.delete(this.uri + match.id).then(response => {
        console.log(response.data);
        this.getlistematch();
      });
    }
  },
  mounted() {
    this.getlistematch();
  }
};
</script>


<style>
#Modulematchs {
  background-color: #7f7f7f;
}
.infomatchadd {
  text-align : left;
  margin-right: 30px;
}
.boutonadd {
  height : 30px;
  margin : auto auto;
}

.fieldsetadd {
  margin : auto auto;
  background-color : #a8adfa;
}
</style>