<template>
   <BoxTraker>
        <div class="columns clicavel">
            <div class="column is-4">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column is-3">
                {{ tarefa.projeto?.nome || 'N/D' }}
            </div>
                <div class="column">
                    <CronometroTraker :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
                </div>
        </div>
    </BoxTraker>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroTraker from './CronometroTraker.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxTraker from './BoxTraker.vue';

export default defineComponent({
    name: 'TarefaTraker',
    components: {
        CronometroTraker,
        BoxTraker
    },
    props:{
        tarefa:{
            type: Object as PropType<ITarefa>,
            required: true
        }
    },
    computed: {
    tempoGasto () : string {
      return new Date(this.tarefa.duracaoEmSegundos * 1000)
        .toISOString()
        .substr(11, 8)
    }
  }
})

</script>
<style scoped>
.clicavel{
    cursor: pointer;
}
</style>