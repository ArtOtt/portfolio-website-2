<template>
  <p
    :class="[
      'relative font-mono overflow-hidden whitespace-nowrap text-pretty text-lg font-medium text-gray-500 sm:text-xl/8 transition-opacity slow-fade',
      isVisible ? 'opacity-100' : 'opacity-0',
    ]"
  >
    Anim aute id magna aliqua ad ad non deserunt sunt. Qui irure qui lorem
    cupidatat commodo. Elit sunt amet fugiat veniam occaecat.
  </p>
</template>

<script>
import { ref, onMounted } from "vue";

export default {
  setup() {
    const isVisible = ref(false);

    onMounted(() => {
      setTimeout(() => {
        isVisible.value = true;
      }, 2000); // Verzögerung von 2 Sekunden vor dem Einblenden
    });

    return { isVisible };
  },
};
</script>

<style scoped>
/* Benutzerdefinierte Dauer für langsame Einblendung */
.slow-fade {
  transition-duration: 3s; /* 3 Sekunden für langsame Einblendung */
}
</style>
