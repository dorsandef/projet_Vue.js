<template>
  <div id="voiture">
    <h3>{{voiture.name}}</h3>
    <button v-on:click="showinput = ! showinput">Modifier</button>
    <div v-if="showinput">
    <input type="text" v-model='voiture.name'>
    <button v-on:click='UpdateVoiture(voiture)'>Valider</button>
    </div>
    <button v-on:click="deletevoiture(voiture)">Supprimer</button>
  </div>
</template>

<script>
export default {
  name: "Voiture",
  props: ['voiture'],
  data() {
    return { showinput :false,
    };
  },
  methods: {
      UpdateVoiture(voiture) {
          this.$emit( "event_updatevoiture",voiture)
      },
      deletevoiture(voiture) {
        this.$emit("event_deletevoiture", voiture)
      }
  },
};
</script>


<style>
#voiture {
  background-color : #a8c6fa;
  width: 300px;
  margin : 5px auto;
  padding : 5px;
}
</style>