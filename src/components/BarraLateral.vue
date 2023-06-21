<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>
        <button class="button" @click="alterarTema">
            Modo Escuro
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent} from 'vue'

export default defineComponent({
    name: 'BarraLateral',
    emeits: ['aoTemaAlterado'],
    data(){
      return{
        modoEscuroAtivado: false
      }
    },
    computed:{
      textoBotao (){
        if(this.modoEscuroAtivado){
          return 'Desativar Modo Escuro'
        }
        else{
          return 'Ativar Modo Escuro'
        }
      }
    },
    methods:{
      alterarTema(){
        this.modoEscuroAtivado =!this.modoEscuroAtivado
        this.$emit('aoTemaAlterado', this.modoEscuroAtivado)
      }
    }
})


</script >

<style scoped>
    header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>