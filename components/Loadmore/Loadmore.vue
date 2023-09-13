<template>
  <div class="loadmore spacer m-top-lg">
    <button @click="loadMore" title="Load More" class="btn btn-primary">Load More</button>
  </div>
</template>

<script>
export default {
  name: 'Loadmore',
  methods: {
    loadMore(){
      this.$emit("load");
    }
  }
}
</script>
