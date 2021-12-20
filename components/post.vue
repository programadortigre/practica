<template>
  <nuxt-link :to="'/post/'+ id">
        <div class="tarjeta">
            <h3>{{id}}</h3>
            <p>{{name}}</p>
        </div>
  </nuxt-link>
</template>
<script>
export default {
    name: 'post',
    props: ['id', 'name']
}
</script>
