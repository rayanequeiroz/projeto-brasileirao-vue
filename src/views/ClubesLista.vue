<template>
    <v-container>
        <h2 class="text-h5 text-center mb-3 mt-5"> Classificação dos clubes</h2>
    <ClubesTabela :clubes="clubesOrdenados"/>
    </v-container>
   
</template>


<script>
//import ClubesTabela from './views/ClubesTabela';

export default {
    name: 'ClubesLista',
    components: {
       // ClubesTabela
    },
    data(){
        return {
            clubesLista: []
        }
    },
    created(){
        fetch('https://hackthon-decola.firebaseio.com/clubes-lista.json')
        .then(response => response.json())
        .then(json => {
            this.clubesLista = json
        })
    },
    computed: {
        clubesOrdenados()  {
            const listaComputada = this.clubesLista.slice(0).sort( (a,b) => a.pontos >b.pontos? -1: 1);
            return listaComputada;
        }
    }
}
</script>

<style scoped>

</style>