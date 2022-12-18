<template>
  <div class="px-4 mx-auto sm:px-6 xl:max-w-5xl xl:px-0 mt-10">
    <div class="flex items-center font-medium mt-6 sm:mx-3 justify-center">
      <nuxt-img
        :src="siteMetadata.author_image"
        loading="lazy"
        alt=""
        class="mr-3 w-10 h-10 rounded-full bg-slate-50 dark:bg-slate-800"
      />
      <div>
        <div class="text-slate-900 dark:text-slate-200">
          {{ siteMetadata.author }}
        </div>
        <a
          target="_blank"
          :href="siteMetadata.twitter"
          class="text-sky-500 hover:text-sky-600 dark:text-sky-400"
        >
          @{{ siteMetadata.twitter_user }}
        </a>
      </div>
    </div>
    <h1 class="text-4xl text-gray-700 font-extrabold mt-10 text-center">
      {{ poem.title }}
    </h1>
    <p class="text-center font-bold my-5 text-indigo-500">
      {{ poem.tags }}
    </p>
    <div class="items-center flex flex-col w-full">
      <nuxt-content class="prose flex flex-col self-center my-auto p-10" :document="poem" />
    </div>
  </div>
</template>
<script>
import Prism from "~/plugins/prism";
import siteMetaInfo from "@/data/sitemetainfo";
export default {
  data() {
    return {
      title: 0,
      siteMetadata: siteMetaInfo,
    };
  },
  async asyncData({ $content, params }) {
    const poem = await $content("poems", params.slug).fetch();
    return {
      poem: poem,
    };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
  mounted() {
    Prism.highlightAll();
  },
  head() {
    //console.log(this.poem.title);
    return {
      title: this.poem.title,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.poem.description,
        },
      ],
    };
  },
};
</script>
<style>
.nuxt-content h2 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content p {
  margin-bottom: 20px;
}
</style>
