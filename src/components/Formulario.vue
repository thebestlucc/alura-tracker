<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <div
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
          <Temporizador @aoTemporizadorFinalizado="finalizarTarefa" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from "./Temporizador.vue";

export default defineComponent({
  name: "FormularioTarefas",
  emits: ["aoSalvarTarefa"],
  components: {
    Temporizador,
  },
  data() {
    return { descricao: "" };
  },
  methods: {
    finalizarTarefa(duracaoEmSegundos: number): void {
      this.$emit("aoSalvarTarefa", {
        descricao: this.descricao,
        duracaoEmSegundos: duracaoEmSegundos,
      });
      this.descricao = "";
    },
  },
});
</script>

<style>
.formulario {
  color: var(--texto-primario);
  background: var(--bg-primario);
}
</style>
