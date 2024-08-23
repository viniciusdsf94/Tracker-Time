<template>
    <button class="button" @click="clicado" :disabled="cronometroRodando">
        <span class="icon">
        <i :class="icone"></i>
      </span>
      <span>
        {{ texto }}
      </span>
    </button>
</template>
<script lang="ts">

    import {defineComponent} from 'vue'

    export default defineComponent({
        name:"Botão",
        emit:['clicado'],
        props:{
            texto:String,
            icone: String,
            cronometroRodando:{
                type: Boolean
            }
        },
        methods:{
            clicado(){
                this.$emit('clicado')
            }
        }
    })

</script>
