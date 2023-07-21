<template>
  <section>
    <strong class="display">{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CronometroComponent",
  props: {
    duracaoEmSegundos: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    tempoDecorrido(): string {
      console.log(this.$props.duracaoEmSegundos);

      return new Date(this.duracaoEmSegundos * 1000)
        .toISOString()
        .substring(11, 19);
    },
  },
});
</script>
<style scoped>
.display {
  color: var(--texto-primario);
}
</style>
