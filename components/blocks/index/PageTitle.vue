<template>
    <section id="page-title" class="block">
        <div class="wrapper">
            <div class="title">
                <h1>{{title}}</h1>
            </div>

            <div class="spacer p-top-lg no-space">
                <nuxt-link title="Services" class="btn btn-lg btn-link btn-line line-active p-0 border-0 min-w-auto link-no-space spacer m-right-xs" to="/programs">Programs</nuxt-link>
                <nuxt-link title="Contacts" class="btn btn-lg btn-link btn-line p-0 border-0 min-w-auto link-no-space" to="/contacts">Contacts</nuxt-link>
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
            default: "'"
          }
        }
    }
</script>
