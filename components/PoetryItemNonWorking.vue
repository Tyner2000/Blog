<template>
  <div>
    <div class="p-4 md:w-1/2 md" style="max-width: 544px">
      <div class="h-full overflow-hidden border-2 border-gray-200 rounded-md border-opacity-60 dark:border-gray-700">
        <div class="p-6">
          <h3 class="mb-4 text-2xl text-slate-700 tracking-tight font-bold dark:text-slate-200">
            <NuxtLink :to="{ name: 'poem-slug', params: { slug: postSlug } }">
              {{ postTitle }}</NuxtLink
            >
          </h3>
          <div class="mb-6 prose prose-slate dark:prose-dark">
            <p>
              {{ postDescription }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["title", "description", "date", "slug"],
  data() {
    return {
      postTitle: this.title,
      postDescription: this.description,
      postSlug: this.slug,
      postDate: this.date,
    };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>

<style></style>
