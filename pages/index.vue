<template>
  <section>
    <NuxtLink to="/CopywritingPage">Copywriting Page</NuxtLink>
    <slice-zone type="page" uid="home" />
  </section>
</template>

<script>
import SliceZone from 'vue-slicezone'
export default {
  components: {
    SliceZone,
  },
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
