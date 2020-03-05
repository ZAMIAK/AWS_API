<template>
<div>
    <h2>Liste de fichiers</h2>
    <ul>
        <li>sdsdsd</li>
        <li>{{nomFichier}}</li>
    </ul>
</div>
</template>
<script>
export default {
    name: 'todos',
    data(){
        return{
            nomFichier: null
        }
    },
    mounted(){
        this.$http.get("https://czrnafchb7.execute-api.eu-west-3.amazonaws.com/mrcfa/")
        .then(response => this.nomFichier = response.data.body)
    }
}
</script>
<style scoped>

</style>