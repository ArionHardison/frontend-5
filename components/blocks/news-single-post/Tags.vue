<template>
    <div class="tags">
        <p>
          <template v-for="tag in tags">
            <nuxt-link :title="tag.tag_name" :to="`/programs/0-all-categories/${tag.id}-${tag.tag_name}`">{{tag.tag_name}}</nuxt-link>
          </template>
        </p>
    </div>
</template>

<script>
    export default {
        name: 'Tags',
        props: {
          tags: {
            type: Array,
            default: [],
          }
        }
    }
</script>
