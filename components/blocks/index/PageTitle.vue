<template>
    <section id="page-title" class="block">
        <div class="wrapper">
            <div class="title">
                <h1>Events organization with our <br>professional team.</h1>
            </div>

            <div class="spacer p-top-lg no-space">
                <router-link title="Services" class="btn btn-lg btn-link btn-line line-active p-0 border-0 min-w-auto link-no-space spacer m-right-xs" to="/services">Services</router-link>
                <router-link title="Contacts" class="btn btn-lg btn-link btn-line p-0 border-0 min-w-auto link-no-space" to="/contacts">Contacts</router-link>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'PageTitle'
    }
</script>
