<template>
<form action="" method="post" v-on:submit.prevent="submit()" enctype="multipart/form-data">
    <p>Nom :</p>
    <input type="text" v-model="Nom">
    <p>Image :</p>
    <input type="text" v-model="Image">
    <!-- <input type="file" @change="addFile"> -->
    <p>chaleur :</p>
    <input type="text" v-model="Chaleur">
    <p>froid :</p>
    <input type="text" v-model="Froid">
    <p>arrosage(en jour) :</p>
    <input type="number" v-model="Arrosage">
    <p>exposition :</p>
    <input type="text" v-model="Exposition">
    
    <button>Créer</button>
</form>
  
</template>

<script>
export default {
    emits:['ajouterFleur'],
    data() {
        return {
            Nom:'',
            Image:'',
            Chaleur:'',
            Froid:'',
            Arrosage:0,
            Exposition:'',
        }
    },
    methods: {
        submit(){
            this.$emit('ajouterFleur',this.Nom,this.Image,this.Chaleur,this.Froid,this.Arrosage,this.Exposition);
            this.Nom ='';
            this.Image ='';
            this.Chaleur ='';
            this.Froid ='';
            this.Exposition ='';
            this.Arrosage=0;

        },
        addFile(event) {
            console.log(event);
   }
    },

    

}
</script>

<style>

</style>