<template>
  <manin class="columns is-gapless is-multiline">
    <div class="column is-one-quarter" >
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter" >
      <FormularioTraker @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaTraker v-for=" (tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      

      </div>
    </div>
  </manin>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTraker from './components/FormularioTraker.vue';
import TarefaTraker from './components/TarefaTraker.vue';
import ITarefa from './interfaces/ITarefa';

export default defineComponent({
    name: "App",
    components: {
      BarraLateral,
      FormularioTraker,
      TarefaTraker
    },
    data(){
      return {
        tarefas: [] as ITarefa[]
      }
    },
    methods:{
      salvarTarefa(tarefa : ITarefa){
        this.tarefas.push(tarefa)
      }
    }

});
</script>

<style> 
.lista{
    padding:1.25rem;
}

</style>
