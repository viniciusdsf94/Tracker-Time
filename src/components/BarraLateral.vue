<template>
    <Header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>
        <button class="button" @click="AlterarTema">{{ textoBotao }}</button>
    </Header>

    
</template>

<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BarraLateral',
    emits:["TemaAlterado"],
    data() {
        return{
            modoEscuro:false
        }
    },
    methods:{

        AlterarTema(){
            this.modoEscuro = !this.modoEscuro
            this.$emit("TemaAlterado", this.modoEscuro)
        },
    },
    computed:{
        textoBotao(){
            if(this.modoEscuro){
             return "Desativar modo escuro"
            }
              return "Ativar modo escuro"
        }   
        }
       
})
</script>

<style scoped>
    header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    }
    @media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
    }
</style>