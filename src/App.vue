<template>
  <NavBar />
  <HeroSection />

  <div
    class="bg-white mx-auto max-w-4xl p-10 mt-[200px] mb-[100px] flex flex-col items-center gap-10 shadow-lg rounded-lg"
  >
    <img
      src="https://cdn.pixabay.com/photo/2016/09/24/03/20/man-1690965_1280.jpg"
      alt="Profilbild"
      class="w-48 h-56 rounded-lg object-cover shadow-md mb-6"
    />

    <div class="flex flex-col md:flex-row w-full gap-10">
      <div class="md:w-1/2">
        <h2 class="text-3xl font-semibold text-gray-800 mb-5">About Me</h2>
        <p class="text-gray-600 leading-relaxed text-sm">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi
          eligendi deserunt recusandae ut tenetur reprehenderit rerum! Odio ab,
          quia ratione distinctio eveniet magnam optio suscipit fugit asperiores
          soluta numquam exercitationem? Lorem ipsum dolor sit amet consectetur
          adipisicing elit.
          <br /><br />
          Animi eligendi deserunt recusandae ut tenetur reprehenderit rerum!
          Odio ab, quia ratione distinctio eveniet magnam optio suscipit fugit
          asperiores soluta numquam exercitationem?
        </p>
      </div>

      <div class="md:w-1/2 space-y-6">
        <h2 class="text-3xl font-semibold text-gray-800 mb-5">Skills</h2>

        <div class="w-full space-y-4">
          <div class="flex items-center">
            <span class="text-sm font-medium text-blue-700 w-1/3">HTML</span>
            <div class="bg-gray-200 rounded-full h-3 w-2/3 overflow-hidden">
              <div
                class="bg-blue-600 h-3 rounded-full transition-all duration-300"
                style="width: 80%"
              ></div>
            </div>
          </div>

          <div class="flex items-center">
            <span class="text-sm font-medium text-blue-700 w-1/3">CSS</span>
            <div class="bg-gray-200 rounded-full h-3 w-2/3 overflow-hidden">
              <div
                class="bg-blue-600 h-3 rounded-full transition-all duration-300"
                style="width: 70%"
              ></div>
            </div>
          </div>

          <div class="flex items-center">
            <span class="text-sm font-medium text-blue-700 w-1/3"
              >JavaScript</span
            >
            <div class="bg-gray-200 rounded-full h-3 w-2/3 overflow-hidden">
              <div
                class="bg-blue-600 h-3 rounded-full transition-all duration-300"
                style="width: 60%"
              ></div>
            </div>
          </div>

          <div class="flex items-center">
            <span class="text-sm font-medium text-blue-700 w-1/3">Vue.js</span>
            <div class="bg-gray-200 rounded-full h-3 w-2/3 overflow-hidden">
              <div
                class="bg-blue-600 h-3 rounded-full transition-all duration-300"
                style="width: 50%"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from "./components/Hero/NavBar.vue";
import HeroSection from "./components/Hero/HeroSection.vue";

export default {
  components: { NavBar, HeroSection },
};
</script>
<style scoped></style>
