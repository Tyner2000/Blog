<template>
  <div class="p-4 w-full md:w-1/2 mx-auto" style="max-width: 544px">
    <div class="h-full overflow-hidden border-2 border-gray-200 rounded-md border-opacity-60 dark:border-gray-700">
      <div class="p-6">
        <div class="flex flex-row justify-between items-center">
          <NuxtLink :to="{ name: 'poem-slug', params: { slug: poemSlug } }">
            <h2 class="text-2xl font-bold leading-8 tracking-tight mb-3">
              {{ poemTitle }}
            </h2>
          </NuxtLink>
          <div class="bg-red-500 pl-2 pr-2 text-sm dark:text-slate-400 font-bold text-white rounded-md">
            <NuxtLink :to="{ name: 'poem-slug', params: { slug: poemSlug } }">
              Read More
            </NuxtLink>
          </div>
        </div>
        </NuxtLink>
        <div>
          <p class="prose text-gray-500 max-w-none dark:text-gray-400 mb-3">
            {{ poemDescription }}
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
      poemTitle: this.title,
      poemDescription: this.description,
      poemSlug: this.slug,
      poemChapter: this.tags,
    };
  },
};
</script>

<style></style>
