<script>
import HeroButtons from "./HeroButtons.vue";
import HeroPicture from "./HeroPicture.vue";
import HeroText from "./HeroText.vue";
import Typewriter from "./Typewriter.vue";

export default {
  components: { Typewriter, HeroText, HeroButtons, HeroPicture },
};
</script>

<template>
  <div class="bg-white">
    <div class="relative isolate px-6 pt-20 lg:px-8">
      <div class="mx-auto max-w-2xl py-32 sm:py-48 lg:py-45">
        <div class="text-center">
          <HeroPicture />
          <Typewriter />

          <HeroText />
          <HeroButtons />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
