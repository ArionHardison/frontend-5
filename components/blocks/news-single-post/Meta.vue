<template>
    <div class="meta">
        <p>
            <span class="date">29 April, 2020</span>
            <span>
                <router-link to="/news-single-post">By admin</router-link>
            </span>
            <span>-</span>
            <span>Comments (1)</span>
            <span>-</span>
            <span class="category">
                <router-link title="Event" to="/news">Event</router-link>
            </span>
        </p>
    </div>
</template>

<script>
    export default {
        name: 'Meta'
    }
</script>
