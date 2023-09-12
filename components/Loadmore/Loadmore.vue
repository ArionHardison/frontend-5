<template>
    <div class="loadmore spacer m-top-lg">
        <a @click="scrollToSection('#news-index')" title="Load More" class="btn btn-gradient" id="loadmore"  href="#news-index">Load more</a>
    </div>
</template>

<script>
    export default {
        name: 'Loadmore'
    }
</script>
