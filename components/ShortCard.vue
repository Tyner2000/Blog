<template>
  <div class="p-4 w-full md:w-1/2 mx-auto" style="max-width: 544px">
    <div class="h-full overflow-hidden border-2 border-gray-200 rounded-md border-opacity-60 dark:border-gray-700">
      <div class="p-6">
        <div class="flex flex-row justify-between items-center">
          <NuxtLink :to="{ name: 'short-slug', params: { slug: shortSlug } }">
            <h2 class="text-2xl font-bold leading-8 tracking-tight mb-3">
              {{ shortTitle }}
            </h2>
          </NuxtLink>
          <NuxtLink :to="{ name: 'short-slug', params: { slug: shortSlug } }">
            <div class="bg-red-500 pl-2 pr-2 text-sm dark:text-slate-400 font-bold text-center text-white rounded-md">
              Continued
            </div>
          </NuxtLink>
        </div>
        <div>
          <p class="prose text-justify text-gray-500 max-w-none dark:text-gray-400 mb-3">
            {{ shortDescription }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "description", "slug", "tags"],
  data() {
    return {
      shortTitle: this.title,
      shortDescription: this.description,
      shortSlug: this.slug,
      shortChapter: this.tags,
    };
  },
};
</script>

<style></style>
