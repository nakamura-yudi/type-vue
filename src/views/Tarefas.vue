<template>
    <FormularioTraker @aoSalvarTarefa="salvarTarefa"/>
    <div class="lista">
        <BoxTraker v-if="semTarefas">
            Você não está muito produtivo hoje <span class="has-text-weight-bold">:(</span>
        </BoxTraker>
        <TarefaTraker v-for="(tarefa, index) in tarefas" :tarefa="tarefa" :key="index"/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import FormularioTraker from "../components/FormularioTraker.vue";
import BoxTraker from "../components/BoxTraker.vue";
import TarefaTraker from "@/components/TarefaTraker.vue";
import ITarefa from "../interfaces/ITarefa"

export default defineComponent({
  name: "App",
  components: {
    BoxTraker,
    FormularioTraker,
    TarefaTraker
  },
  data () {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  methods: {
    salvarTarefa (tarefa:ITarefa) : void {
      this.tarefas.push(tarefa)
    }
  },
  computed: {
    semTarefas () :boolean {
      return this.tarefas.length == 0
    }
  }
});
</script>