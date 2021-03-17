<template>
  <div class="pt-60 container">
    <slice-zone type="page" :uid="$route.params.uid" class="flex flex-col" />
  </div>
</template>

<script>
import SliceZone from 'vue-slicezone'

export default {
  components: {
    SliceZone,
  },
}
</script>
