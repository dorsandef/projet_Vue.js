<template>
  <div id="match">
    <div id="MatchModule">
      <div class="infomatch">
        <h2>{{ match.titre}}</h2>
        <p>
          <em>
            <strong>Horaire:</strong>
          </em>
          Le {{match.date}} à {{match.heure}}
        </p>
        <p>
          <em>
            <strong>Adresse</strong>
          </em>
          : {{match.adresse}}
        </p>
        <p>
          <em>
            <strong>Voiture du jour</strong>
          </em>
          : {{match.matchvoiture}}
        </p>
      </div>
    </div>
<button v-on:click="deletematch(match)">Supprimer</button>
    <button v-on:click="showinput = ! showinput">Modifier</button>
    <div v-if="showinput">
      <fieldset>
        <legend><strong>Modification Match :</strong> </legend> 
        <div class="infomatchupdate">
      Titre: <input type="text" v-model="match.titre" /> <br>
      Date: <input type="date" v-model="match.date" /> <br>
      Heure: <input type="time" v-model="match.heure" /> <br>
      Adresse: <input type="text" v-model="match.adresse" /> <br>
      Voiture du jour: <input type="text" v-model="match.matchvoiture" /> <br>
        joueur1: <input size='12' type="text" v-model="joueur1" />
        joueur2: <input size='12' type="text" v-model="joueur2" />
        joueur3: <input size='12' type="text" v-model="joueur3" />
        joueur4: <input size='12' type="text" v-model="joueur4" />
        joueur5: <input size='12' type="text" v-model="joueur5" />
        joueur6: <input size='12' type="text" v-model="joueur6" />
        </div>
      <button class="updatebutton" v-on:click="UpdateMatch(match)">Valider</button>
      </fieldset>
    </div>
  </div>
</template>

<script>
export default {
  name: "Match",
  props: ["match"],
  data() {
    return { showinput: false };
  },
  methods: {
    UpdateMatch(match) {
      this.$emit("event_updatematch", match);
    },
    deletematch(match) {
      this.$emit("event_deletematch", match);
    }
  }
};
</script>


<style>
#match {
  background-color : #a8c6fa;
  width: 900px;
  margin: 15px auto;
  padding: 5px;
  border: solid;
}

p {
    text-align: left;
}

#MatchModule {
  display: flex;
  background-color : #a8c6fa;
  height: 250px; 
}

.infomatch {
    width : 550px;
}
     
input {
  border : solid 0.1px;
  border-radius : 1px;
}

fieldset {
  display: flex;
  width : 870px;
  height: 200px;
  background-color : #a8adfa;
  border-radius : 3px;
}

.infomatchupdate {
  text-align : left;
  margin-right: 30px;
}

.updatebutton {
  height : 30px;
  margin : auto auto;
}

.infomatch {
    width : 550px;
}
</style>