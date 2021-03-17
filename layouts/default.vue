<template>
  <div>
    <NavBar />
    <main id="main" class="main">
      <nuxt />
    </main>
  </div>
</template>
<script>
export default {
  // Called before rendering the layout (even for error page)
  async middleware({ store, $prismic }) {
    await store.dispatch('fetchMenu', $prismic)
  },
  head() {
    return {
      title: 'Prismic Nuxt.js Multi Page Website',
    }
  },
}
</script>

<style>
/* can't be empty */
</style>
