

<template>
    <Box>
         <div class="columns">
            <div class="column is-7">
                {{ tarefa?.descricao }}
            </div>
            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa?.duracaoEmSegundos"/> 
            </div>
         </div>
    </Box>
</template>

<script  lang="ts">

import Cronometro from './Cronometro.vue';
import ITarefa from '../interfaces/ITarefa';
import { PropType } from 'vue';

import { defineComponent } from 'vue';
import Box from './Box.vue';
export default defineComponent({
    name:"Tarefa",
    props:{
        tarefa: Object as PropType<ITarefa>,
        
    },

    components:{
        Cronometro,
        Box
    }
})


</script>

<style scoped>
   .box{
    background:#FAF0CA;
   }
</style>