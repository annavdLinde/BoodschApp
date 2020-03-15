<!--html -->
<template>
  <div id="app">
    <Header/>
    <BoodschappenToevoegen v-on:boodschap-toevoegen="boodschapToevoegen"/>
    <Boodschappen v-bind:boodschappen="boodschappen"
                  v-on:del-boodschap="BoodschapVerwijderen"
                  v-on:boodschap-aangevinkt="Aangevinkt"
                  v-on:boodschap-omhoog="BoodschapOmhoog"
                  v-on:boodschap-omlaag="BoodschapOmlaag"
    />
  </div>
</template>

<!--Javascript-->
<script>
 import Header from "./components/layout/Header";
 import BoodschappenToevoegen from "./components/BoodschappenToevoegen";
 import Boodschappen from "./components/Boodschappenlijst";

export default {
  name: 'App',
  components: {
    Header,
    BoodschappenToevoegen,
    Boodschappen
  },
  data (){
    return {
      boodschappen: [
        {
          id: 1,
          title: "Sars",
          completed: false
        },
        {
          id: 2,
          title: "Malaria",
          completed: false
        },
        {
          id: 3,
          title: "Covid-19",
          completed: false
        },
        {
          id: 4,
          title: "Mazelen",
          completed: false
        },
        {
          id: 5,
          title: "Pfeiffer",
          completed: false
        }
      ]
    }
  },
  methods: {
    BoodschapVerwijderen(id){
      this.boodschappen = this.boodschappen.filter(boodschap => boodschap.id !== id);
    },
    boodschapToevoegen(nieuweBoodschap){
      this.boodschappen = [...this.boodschappen, nieuweBoodschap];
    },
    Aangevinkt(){
      this.boodschappen = this.boodschappen.sort(function(a,b){
        if (a.completed === b.completed){
          return 0;
        }
        if (a.completed === false && b.completed === true){
          return -1;
        }
        return 1;
      });
    },
    BoodschapOmhoog(index){
      let geselecteerdeBoodschap = this.boodschappen[index];
      this.boodschappen.splice(index,1);
      if (index == 0) {
        index =1;
      }
      this.boodschappen.splice((index-1), 0, geselecteerdeBoodschap);
      console.log(index);
    },
    BoodschapOmlaag(index){
      let geselecteerdeBoodschap = this.boodschappen[index];
      this.boodschappen.splice(index,1);
      this.boodschappen.splice((index+1), 0, geselecteerdeBoodschap);
      console.log(index);
    }
  }
}
</script>

<!--CSS-->
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
