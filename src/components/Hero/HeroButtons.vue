<template>
  <div class="mt-10 flex items-center justify-center gap-x-6">
    <!-- Erster Button: Langsames Einblenden -->
    <a href="#" v-show="showButtons" class="button opacity-0 animation-fade-in">
      Get started
    </a>

    <!-- Zweiter Button: Langsames Einblenden -->
    <a
      href="#"
      v-show="showButtons"
      class="button-secondary opacity-0 animation-fade-in"
    >
      Learn more <span aria-hidden="true">→</span>
    </a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showButtons: false,
    };
  },
  mounted() {
    // Beide Buttons werden nach 3 Sekunden Verzögerung gleichzeitig langsam eingeblendet
    setTimeout(() => {
      this.showButtons = true;
    }, 3000); // Verzögerung vor dem Einblenden
  },
};
</script>

<style scoped>
/* Definition einer langsamen Fade-In-Animation */
@keyframes fadeInSlow {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

/* Anwendung der Fade-In-Animation über 8 Sekunden */
.animation-fade-in {
  animation: fadeInSlow 3s forwards;
}

/* Tailwind-Klassen für die Buttons */
.button {
  @apply rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus:outline focus:outline-2 focus:outline-offset-2 focus:outline-indigo-600;
}

.button-secondary {
  @apply text-sm font-semibold text-gray-900;
}
</style>
