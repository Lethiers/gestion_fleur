<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->

<h1>Liste des Plantes:</h1>

<button v-on:click="afficherFleur"> ajouter une fleur </button>


<AjouterFleur v-if="visible" v-on:ajouterFleur="ajouterFleur"></AjouterFleur>

<ul v-for="(item, index) in lesFleurs" :key="index">
<ListeFleur
:id="item.id"
:LeNom="item.nom"
:Image="item.Image"
:Froid="item.froid"
:Chaud="item.chaud"
:Exposition="item.exposition"
:Arrossage="item.arrossage"
v-on:supprimerFleur="effacerFleur"

></ListeFleur>

</ul>
</template>

<script>
import ListeFleur from './components/ListeFleur.vue';
import AjouterFleur from './components/AjouterFleur.vue';


export default {
  name: 'App',
  components: {
    ListeFleur,
    AjouterFleur,
},
data() {
  return {
    visible:false,
    lesFleurs:[{
      id:1,
      nom:'Abricot',
      Image:"https://res.cloudinary.com/hv9ssmzrz/image/fetch/c_fill,f_auto,h_240,q_auto,w_325/https://images-ca-1-0-1-eu.s3-eu-west-1.amazonaws.com/photos/original/734/abricot-coupe-3000x2000.jpg",
      chaleur:5,
      froid:8,
      arrossage:7,
      exposition:'sud-est'
    },
    {
      id:2,
      nom:'Menthe',
      Image:"https://www.fermedelours.fr/wp-content/uploads/2021/01/menthe-ppoivree-min-300x300.jpg",
      chaleur:5,
      froid:8,
      arrossage:7,
      exposition:'sud-est'

    },
    {
      id:3,
      nom:'Fleur',
      Image:"https://i.ebayimg.com/images/g/3JUAAOSw~8ldvpxi/s-l500.png",
      chaleur:5,
      froid:8,
      arrossage:7,
      exposition:'sud-est'

    }
    ]
  }
},
methods:{
  ajouterFleur(nom,image,chaleur,froid,arrossage,exposition){
    const ajouterFleur = {id:new Date().toISOString(),nom:nom,Image:image,chaud:chaleur,froid:froid,arrossage:arrossage,exposition:exposition};
    this.lesFleurs.push(ajouterFleur);  
    console.log(this.lesFleurs);
  },
  effacerFleur(id){
    this.lesFleurs = this.lesFleurs.filter((uneFleure)=>uneFleure.id !== id);
  },
  afficherFleur(){
    this.visible = !this.visible;
    console.log(this.visible);
  }
}
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
