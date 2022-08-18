<template>
        <div>
        <h2>{{LeNom}}:</h2>
        <!-- <img src="./src/assets/image/abricot.jpg" alt=""> -->
        <!-- <img :src="require(Image)" alt="">{{Image}} -->
        <img :src="Image" alt="">
        <ul v-if="visible == true">
        <p>sensible à la chaleur: {{Chaud}}</p>
        <p>sensible au froid: {{Froid}}</p>
        <p>idéalement situé : {{Exposition}}</p>
        <p>arroser tout les {{Arrossage}} jours</p>
        <p>dernier arrosage {{this.timer}} jours</p>
        
        </ul>
        <button v-on:click="afficherDetail()">détails</button>
        <button v-on:click="arroser()">arroser</button>
        <button v-on:click="$emit('supprimerFleur',id)">supprimer</button>
    </div>

</template>

<script>
export default {
  emits:['supprimerFleur'],
    props:{
        LeNom:{type:String,require:true},
        Image:{type:String,require:true},
        Froid:{type:String,require:true},
        Chaud:{type:String,require:true},
        Exposition:{type:String,require:true},
        Arrossage:{type:Number,require:true},
        id:{type:String,require:true},
    },
    data() {
        return {
            visible:false,
            test: 0,
            timer:0,
        }
    },
    methods: {
        afficherDetail(){
            console.log('ok');
            this.visible = !this.visible;
        },
        arroser(){
            const date = Date.now();
            this.test = date;

            let arrive = this.test;
            let depart = this.test + this.Arrossage;
            this.timer = depart - arrive;
            console.log(this.timer);
        }
    },

}



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>