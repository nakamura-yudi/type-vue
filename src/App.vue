<template>
  <manin class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivado }">
    <div class="column is-one-quarter" >
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo" >
      <FormularioTraker @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaTraker v-for=" (tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <Box v-if="listaEstaVazia">
          Você Nao criou nenhuma tarefa ainda!!!
        </Box>
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
import Box from './components/Box.vue';

export default defineComponent({
    name: "App",
    components: {
      BarraLateral,
      FormularioTraker,
      TarefaTraker,
      Box
    },
    data(){
      return {
        tarefas: [] as ITarefa[],
        modoEscuroAtivado: false
      }
    },
    computed:{
      listaEstaVazia():boolean{
        return this.tarefas.length ===0
      }
    },
    methods:{
      salvarTarefa(tarefa : ITarefa){
        this.tarefas.push(tarefa)
      },
      trocarTema(modoEscuroAtivado : boolean){
        this.modoEscuroAtivado = modoEscuroAtivado
      }
    }

});
</script>

<style> 
.lista{
    padding:1.25rem;
}
main{
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.modo-escuro{
  --bg-primario:#2b2d42;
  --texto-primario: #ddd;
}

.conteudo{
  background-color: var(--bg-primario);
}

</style>
