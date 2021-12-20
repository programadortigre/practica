<template>
  <article>
    <h2 class="font-display font-bold text-4xl mb-16 text-gray-800">
      {{ post.title }}
    </h2>
    <figure class="mb-4">
      <img :src="post.media" alt="" />
    </figure>

    <NuxtContent
      class="prose prose-sm sm:prose lg:prose-lg xl:prose-2xl "
      :document="post"
    />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const slug = params.slug;
    const post = await $content('portafolio', slug).fetch();

    return {
      post,
    };
  },
};
</script>

<style></style>
