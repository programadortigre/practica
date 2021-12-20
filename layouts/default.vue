<template>
  <div>
    <div>
    <navigation />
    </div>
    <Nuxt />
  </div>
</template>

<script>
import navigation from "../components/navigation";
export default {
  components: {
    navigation,
  },
};
</script>
<style>
* {
  box-sizing: border-box;
}
.tarjeta {
  background: red;
}
</style>