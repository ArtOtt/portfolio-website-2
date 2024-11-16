<template>
  <header class="absolute inset-x-0 top-0 z-50">
    <nav
      class="flex items-center justify-center p-6 lg:px-8"
      aria-label="Global"
    >
      <div class="lg:flex lg:gap-x-12 sm:hidden">
        <a
          v-for="(item, index) in navItems"
          :key="index"
          href="#"
          class="text-sm font-semibold text-gray-900 transition-opacity duration-500"
          :class="{ 'opacity-0': !item.visible, 'opacity-100': item.visible }"
        >
          {{ item.text }}
        </a>
      </div>
    </nav>
  </header>
</template>

<script>
import { ref, onMounted } from "vue";

export default {
  setup() {
    // Navigation items with individual delays and initial visibility set to false
    const navItems = ref([
      { text: "Product", visible: false, delay: 300 }, // Delay in milliseconds
      { text: "Features", visible: false, delay: 600 },
      { text: "Marketplace", visible: false, delay: 900 },
      { text: "Company", visible: false, delay: 1200 },
    ]);

    // On component mount, reveal each item after its specific delay
    onMounted(() => {
      navItems.value.forEach((item) => {
        setTimeout(() => {
          item.visible = true;
        }, item.delay); // Use the individual delay for each item
      });
    });

    return { navItems };
  },
};
</script>

<style scoped>
/* Optional: Additional styling for smooth transitions */
</style>
