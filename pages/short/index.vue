<template>
  <div class="max-w-3xl px-4 mx-auto sm:px-6 xl:max-w-5xl xl:px-0">
    <header class="pt-16 pb-9 sm:pb-16 sm:text-center">
      <h1 class="mb-4 text-3xl md:text-4xl tracking-tight text-slate-800 font-extrabold dark:text-slate-200">
        Short-Form Content.
      </h1>
      <p class="text-lg text-slate-700 dark:text-slate-400">
        One-off and serialized works alike.
      </p>
    </header>
    <main class="relative mb-auto">
      <div class="">
        <div class="container py-12">
          <div class="flex flex-wrap -m-4">
            <ShortCard
              v-for="short in shorts"
              :key="short.title"
              :title="short.title"
              :description="short.description"
              :date="short.date"
              :slug="short.slug"
            ></ShortCard>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const shorts = await $content("shorts")
      .only([
        "title",
        "description",
        "img",
        "slug",
        "tag",
        "author",
        "date",
        "draft",
      ])
      .sortBy("date", "asc")
      .fetch();

    return {
      shorts,
    };
  },
  head: {
    title: "Tyner | Short-Form Content.",
    meta: [
      { charset: "utf-8" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        hid: "description",
        name: "description",
        content: "Its Solaiman's Pen and Paper to write ",
      },
    ],
    link: [{ rel: "icon", type: "image/x-icon", href: "/favicon.ico" }],
  },
};
</script>

<style></style>
