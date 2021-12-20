<template>
  <div>
    <h2 class="">
      Blog
    </h2>
    <section class="">
      <article
        v-for="post in articles"
        :key="post.title"
        class=""
        :style="{ aspectRatio: 2 / 1 }"
      >
        <NuxtLink :to="post.path">
          <figure class="absolute inset-0">
            <img :src="post.media" :alt="post.title" />
          </figure>
          <div
            class=""
          ></div>
          <h3
            class=""
          >
            {{ post.title }}
          </h3>
          <span
            class=""
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
    const articles = await $content('blog').fetch();

    return {
      articles: articles.map(({ createdAt, ...rest }) => ({
        ...rest,
        date: $dateFns.format(createdAt, 'yyyy-MM-dd'),
 
      })),
    };
  },
};
</script>
