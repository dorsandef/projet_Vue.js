<template>
  <div id="joueur">
    <h3>{{joueur.firstname}} {{joueur.lastname}} {{joueur.classement}}</h3>
    <!-- permet de basculer entre voir ou pas voir l'input pour la modification -->
    <button v-on:click="showinput = ! showinput">Modifier</button>
    <!-- permet de cacher le bouton si false -->
      <div v-if="showinput">
      <input type="text" v-model='joueur.firstname'>
      <input type="text" v-model='joueur.lastname'>
      <input type="text" v-model='joueur.classement'>
      <button v-on:click='UpdateJoueur(joueur)'>Valider</button>
      </div>
    <button v-on:click="deletejoueur(joueur)">Supprimer</button>
  </div>
</template>

<script>
export default {
  name: "Joueur",
  props: ['joueur'],
  data() {
    return { showinput : false,
    };
  },
  methods: {
      UpdateJoueur(joueur) {
        //on émet un evenement 
        this.$emit( "event_updatejoueur",joueur)
      },
      deletejoueur(joueur) {
        this.$emit("event_deletejoueur", joueur)
      }
  },
};
</script>

<style>
#joueur {
  background-color : #a8c6fa;
  width: 300px;
  height: 90px;
  margin : 5px auto;
  padding : 1px;
}
</style>