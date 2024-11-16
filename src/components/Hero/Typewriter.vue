<template>
  <div class="w-full h-[90px] flex justify-center items-center overflow-hidden">
    <h1
      class="text-5xl font-semibold sm:text-7xlleading-[200px] bg-gradient-to-r bg-gradient-to-r from-zinc-600 to-yellow-900 bg-clip-text text-transparent"
    >
      {{ aktuellerText
      }}<span class="opacity-0 text-6xl animate-pulse text-indigo-600">I</span>
    </h1>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";

export default {
  setup() {
    const woerter = [
      "Willkommen auf meiner Website!",
      "Dies ist ein Schreibeffekt.",
      "Vielen Dank fürs Zusehen!", // Der letzte Text, der dauerhaft stehen bleibt
    ];
    const aktuellerText = ref(""); // Reaktive Variable für den aktuellen Text

    // Geschwindigkeits- und Pausenparameter
    const schreibGeschwindigkeit = 100; // Geschwindigkeit für das Schreiben (Millisekunden)
    const loeschGeschwindigkeit = 30; // Geschwindigkeit für das Löschen (Millisekunden)
    const pauseZwischenWoertern = 250; // Pause nach einem Wort (Millisekunden)
    const pauseAmEnde = 2000; // Pause, bevor der letzte Text stehen bleibt

    let i = 0; // Index für das aktuelle Wort
    let j = 0; // Position im aktuellen Wort
    let istLoeschen = false;
    let istFertig = false; // Status, ob der Effekt beendet ist

    const schreiben = () => {
      if (istFertig) return; // Beende die Funktion, wenn der Effekt beendet ist

      const aktuellesWort = woerter[i];
      if (istLoeschen) {
        aktuellerText.value = aktuellesWort.substring(0, j - 1);
        j--;

        if (j === 0) {
          // Wenn das Wort vollständig gelöscht ist
          istLoeschen = false;
          i++; // Zum nächsten Wort wechseln

          // Wenn wir den letzten Text erreicht haben, Animation beenden
          if (i === woerter.length - 1) {
            // Letztes Wort wird getippt und bleibt dann stehen
            istFertig = true;
            setTimeout(() => {
              schreibenLetztesWort();
            }, pauseZwischenWoertern);
            return;
          }

          setTimeout(schreiben, pauseZwischenWoertern); // Pause zwischen Wörtern
          return;
        }

        setTimeout(schreiben, loeschGeschwindigkeit); // Timer für das Löschen
      } else {
        aktuellerText.value = aktuellesWort.substring(0, j + 1);
        j++;

        if (j === aktuellesWort.length) {
          // Wenn das Wort vollständig geschrieben ist
          istLoeschen = true;
          setTimeout(schreiben, pauseZwischenWoertern); // Pause zwischen dem Schreiben und Löschen
          return;
        }

        setTimeout(schreiben, schreibGeschwindigkeit); // Timer für das Schreiben
      }
    };

    // Funktion, um das letzte Wort langsam zu tippen und stehen zu lassen
    const schreibenLetztesWort = () => {
      const letztesWort = woerter[woerter.length - 1];
      if (j < letztesWort.length) {
        aktuellerText.value = letztesWort.substring(0, j + 1);
        j++;
        setTimeout(schreibenLetztesWort, schreibGeschwindigkeit); // Timer für das Schreiben des letzten Wortes
      }
    };

    onMounted(() => {
      schreiben(); // Starte den Schreibeffekt beim Laden der Komponente
    });

    return {
      aktuellerText,
    };
  },
};
</script>

<style scoped>
/* Keine Notwendigkeit für zusätzliches CSS, da Tailwind alles übernimmt */
/* Blinkende Animation für den Cursor */
@keyframes blink {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
}

/* Klasse für blinkenden Cursor */
.animate-blink {
  animation: blink 1ms step-end infinite;
}
</style>
