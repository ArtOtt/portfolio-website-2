<template>
  <div class="">
    <!-- Absolut positioniertes Bild, das nach 2 Sekunden langsam eingeblendet wird -->
    <img
      v-if="showImage"
      src="https://via.placeholder.com/50"
      alt="Beispielbild"
      ref="image"
      class="absolute top-21"
      :style="imageStyle"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      showImage: false,
      opacity: 0, // Bild beginnt unsichtbar
    };
  },
  computed: {
    imageStyle() {
      return {
        width: "350px",
        height: "350px",
        opacity: this.opacity, // Opazität für langsames Einblenden
        position: x - 100,
      };
    },
  },
  mounted() {
    // Setze einen Timer, um das Bild nach 2 Sekunden anzuzeigen und es einzublenden
    setTimeout(() => {
      this.showImage = true; // Bild sichtbar machen
      this.fadeInImage(); // Bild langsam einblenden
    }, 2000);
  },
  methods: {
    // Funktion für das langsame Einblenden des Bildes
    fadeInImage() {
      const duration = 2000; // Dauer der Einblendung in ms (z. B. 2 Sekunden)
      let start = null;
      const fadeIn = (timestamp) => {
        if (!start) start = timestamp;
        const progress = (timestamp - start) / duration;

        // Berechne die neue Opazität basierend auf dem Fortschritt
        this.opacity = Math.min(progress, 1); // Maximaler Wert für die Opazität ist 1

        // Setze die Animation fort, wenn der Fortschritt < 1 ist
        if (progress < 1) {
          requestAnimationFrame(fadeIn);
        }
      };

      // Starte die Einblendanimation
      requestAnimationFrame(fadeIn);
    },
  },
};
</script>

<style scoped>
/* Keine weiteren Styles erforderlich, da das Bild absolut positioniert ist */
</style>
