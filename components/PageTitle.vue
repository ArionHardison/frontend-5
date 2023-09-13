<template>
    <section id="page-title">
        <div class="wrapper">
            <h1>{{title}}</h1>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'PageTitle',
        props: {
          title: {
            type: String,
            default: "Title"
          }
        }
    }
</script>
