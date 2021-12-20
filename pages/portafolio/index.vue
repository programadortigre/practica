<template>
  <div>
    <h2 class="font-display font-bold text-4xl mb-16 text-gray-800">
     portafolio
    </h2>
    <section class="grid md:grid-flow-col md:grid-cols-3 gap-8">
      <article
        v-for="post in articles"
        :key="post.title"
        class="p-4 bg-gray-200 rounded-xl bg-cover relative overflow-hidden cursor-pointer"
        :style="{ aspectRatio: 2 / 1 }"
      >
        <NuxtLink :to="post.path">
          <figure class="absolute inset-0">
            <img :src="post.media" :alt="post.title" />
          </figure>
          <div
            class="overlay bg-black bg-opacity-50 absolute inset-0 hover:bg-opacity-25 transition-all"
          ></div>
          <h3
            class="text-4xl  md:text-xl text-white font-extrabold z-10 absolute"
          >
            {{ post.title }}
          </h3>
          <span
            class="date absolute bottom-0 right-0 m-4 bg-teal-400 text-white font-extrabold text-sm p-2 rounded-xl"
            >{{ post.date }}</span
          >
        </NuxtLink>
      </article>
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, $dateFns }) {
    const articles = await $content('portafolio').fetch();

    return {
      articles: articles.map(({ createdAt, ...rest }) => ({
        ...rest,
        date: $dateFns.format(createdAt, 'MMM yyyy'),
      })),
    };
  },
};
</script>
