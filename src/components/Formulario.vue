<template>
    <div class="box">
      <div class="columns">
        <div
          class="column is-8"
          role="form"
          aria-label="Formulário para criação de uma nova tarefa"
        >
          <input
            type="text"
            class="input"
            v-model="descricao"
            placeholder="Qual tarefa você deseja iniciar?"
            
          />
        </div>
        <div class="column">
          <Temporizador @ao-temporizador-finalizado="finalizarTarefa"/>
        </div>
      </div>
    </div>
  </template>
  
  <script lang="ts">
    import { defineComponent } from "vue";
    import Temporizador from "./Temporizador.vue";
  
  export default defineComponent({
    name: "Formulário",
    emits:["aoSalvarTarefa"],
    components:{
        Temporizador
    },
    data() {
        return {
            descricao : ""
        }
    },
    methods:{
        finalizarTarefa( tempoDecorrido: number) : void{
            this.$emit("aoSalvarTarefa", {
              descricao: this.descricao,
              duracaoEmSegundos: tempoDecorrido
            })
            this.descricao = ""
        }
    }
    
    
    
  });
  </script>