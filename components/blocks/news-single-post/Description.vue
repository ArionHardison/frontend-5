<template>
    <div class="description clearfix">{{description}}</div>
</template>

<script>
    export default {
        name: 'Description',
        props: {
          description: {
            type: String,
            default: ""
          }
        }
    }
</script>
