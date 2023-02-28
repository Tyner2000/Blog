<template>
  <div class="max-w-3xl px-4 mx-auto sm:px-6 xl:max-w-5xl xl:px-0">
    <header class="pt-16 pb-9 sm:pb-16 sm:text-center">
      <h1 class="mb-4 text-4xl tracking-tight text-slate-800 font-extrabold dark:text-slate-200">
        Poetry
      </h1>
      <p class="text-lg text-slate-700 dark:text-slate-400">
        Rhyming words!
      </p>
    </header>
    <main class="relative mb-auto">
      <div class="">
        <div class="container py-12">
          <div class="flex flex-wrap">
            <PoetryItem
              v-for="poem in poems"
              :key="poem.title"
              :title="poem.title"
              :description="poem.description"
              :slug="poem.slug"
              :tags="poem.tags"
            ></PoetryItem>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const poems = await $content("poems")
      .only([
        "title",
        "description",
        "img",
        "slug",
        "author",
        "draft",
        "tags",
      ])
      .sortBy("date", "asc")
      .fetch();

    return {
      poems,
    };
  },
  head: {
    title: "Tyner | Poetry.",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        hid: "description",
        name: "description",
      },
    ],
    link: [{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" }],
  },
};
</script>

<style></style>
