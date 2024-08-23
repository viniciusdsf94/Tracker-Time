<template>
  <main class="columns is-gapless is-multiline" :class="{'teste-escuro' : modoEscuro}">
    <div class="column is-one-quarter">
      <BarraLateral @temaAlterado="alterarTema"/>
      
    </div>
    <div class="column is-three-quarter">
      <Formulario @aoSalvarTarefa = "salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/>
        <Box v-if="listaEstaVazia">Teste</Box>
      </div>
      
    </div>

  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Formulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import ITarefa from './interfaces/ITarefa';
import Box from './components/Box.vue';


export default defineComponent({
  name: 'App',
  components: {
   BarraLateral,
   Formulario,
   Tarefa,
   Box
  },
  data() {
    return{
      tarefas:[] as ITarefa[],
      modoEscuro: false
    }

  },
  computed:{
   listaEstaVazia():boolean{
    return this.tarefas.length === 0
   }
  },

  methods:{
    salvarTarefa(tarefa:ITarefa){
      this.tarefas.push(tarefa )
    },
    alterarTema(estaAtivo : boolean){
      this.modoEscuro = estaAtivo
    }
  }
});
</script>

<style>
.lista{
  padding: 1.5rem;
}
</style>
