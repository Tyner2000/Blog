<template>
  <!-- Section 1 -->
  <section class="w-full px-6 pb-12 antialiased bg-white">
    <div class="mx-auto max-w-8xl">
      <TheHeader />
      <div class="dark:bg-gray-900 mt-6">
        <div class="max-w-screen-lg md:flex mx-auto dark:bg-gray-900">
          <div class="md:w-1/3 p-2 md:flex md:justify-center h-full">
            <AuthorCard />
          </div>
          <div class="md:w-2/3 px-8 h-full">
            <Nuxt />
            <TheFooter />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import TheHeader from "../components/TheHeader.vue";
import TheFooter from "../components/TheFooter.vue";

export default {
  component: {
    TheHeader,
    TheFooter,
  },
};
</script>

<style></style>
