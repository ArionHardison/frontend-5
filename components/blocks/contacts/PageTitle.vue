<template>
    <section id="page-title" class="block">
        <div class="wrapper">
            <div class="title">
                <h1>{{title}}</h1>
            </div>

            <div class="spacer p-top-lg no-space">
                <p>{{description}}</p>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'PageTitle',
        props: {
          title: {
            type: String,
            default: ""
          },
          description: {
            type: String,
            default: ""
          }
        }
    }
</script>
