<template>
    <div
            class="is-flex is-align-items-center is-justify-content-space-between"
          >
            <Cronometro :tempoEmSegundos="tempoEmSegundos" />
            
            
            <Botao 
                texto="play"
                icone="fa fa-play"
                @clicado="iniciar"
                :cronometroRodando = cronometroRodando
                
                />
                <Botao 
                texto="stop"
                icone="fa fa-stop"
                @clicado="finalizar"
                :cronometroRodando = !cronometroRodando
                />    
          </div>
</template>

<script lang="ts">
 import { defineComponent } from "vue";
    import Cronometro from "./Cronometro.vue";
    import Botao from "./Botao.vue";
  
  export default defineComponent({
    name: "Temporizador",
    emits:['aoTemporizadorFinalizado'],
    components:{
        Cronometro,
        Botao
    },
    data () {
      return {
        tempoEmSegundos: 0,
        cronometro: 0,
        cronometroRodando:false
      }
    },
    
    methods: {
      iniciar () {
        // começar a contagem
        // 1 seg = 1000 ms
        this.cronometroRodando = true
        this.cronometro = setInterval(() => {
          this.tempoEmSegundos += 1        
        }, 1000)
      },
      finalizar () {
        clearInterval(this.cronometro)
        this.$emit("aoTemporizadorFinalizado", this.tempoEmSegundos)
        this.tempoEmSegundos = 0
        this.cronometroRodando = false
      }
    }
  });
</script>