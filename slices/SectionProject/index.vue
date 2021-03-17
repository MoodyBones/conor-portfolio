<template>
  <section class="container mx-auto max-w-sm flex flex-col space-y-4 pb-20">
    <div>
      <prismic-image
        :field="slice.primary.image"
        alt="slice.primary.imageAltText"
      />
    </div>
    <span class="border-gray-700 border-b-8 w-16 block"></span>
    <div class="flex flex-col pb-2 border-b-4">
      <div class="flex items-end">
        <prismic-rich-text
          :field="slice.primary.company"
          class="text-3xl uppercase font-bold"
        />
        <span class="pl-2 uppercase text-gray-700">{{
          slice.primary.location
        }}</span>
      </div>
      <span class="text-xl text-gray-700">{{ slice.primary.jobTitle }}</span>
    </div>
    <prismic-rich-text
      :field="slice.primary.title"
      class="text-5xl font-medium"
    />
    <prismic-rich-text
      :field="slice.primary.description"
      class="text-xl text-gray-600 py-4"
    />
    <div class="flex flex-col space-y-2">
      <div
        class="flex items-center space-x-2 text-lg text-gray-700 font-medium uppercase"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          class="w-8 h-8 block"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
          />
        </svg>
        <span>{{ slice.primary.date | prismicDate }}</span>
      </div>
      <div
        class="flex items-center space-x-2 text-lg text-gray-700 font-medium uppercase"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          class="w-8 h-8 block"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
          />
        </svg>
        <prismic-link :field="slice.primary.externalLink"
          ><span>{{ slice.primary.externalLinkLabel }}</span></prismic-link
        >
      </div>
      <div
        class="flex items-center space-x-2 text-lg text-gray-700 font-medium uppercase"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          class="w-8 h-8 block"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M7 20l4-16m2 16l4-16M6 9h14M4 15h14"
          />
        </svg>
        <div v-for="(item, i) in slice.items" :key="`slice-item-${i}`">
          <prismic-link :field="item.RepeatableTagLink">
            <span>{{ item.RepeatableTag }}</span>
          </prismic-link>
        </div>
      </div>
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
