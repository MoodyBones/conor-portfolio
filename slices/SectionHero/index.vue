<template>
  <section
    class="section container mx-auto sm:max-w-screen-md px-2 sm:px-0 py-40"
  >
    <div class="flex flex-col space-y-6">
      <prismic-rich-text
        :field="slice.primary.title"
        class="font-bold text-7xl"
      />
      <prismic-rich-text :field="slice.primary.description" class="text-6xl" />

      <prismic-link :field="slice.primary.buttonLink">
        <span class="uppercase tracking-wide text-2xl">{{
          slice.primary.buttonLabel
        }}</span></prismic-link
      >
    </div>
  </section>
</template>

<script>
export default {
  props: {
    slice: {
      type: Object,
      required: true,
      default() {
        return {}
      },
    },
  },
}
</script>

<style scoped></style>
