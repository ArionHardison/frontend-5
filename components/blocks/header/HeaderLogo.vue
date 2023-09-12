<template>
    <div class="header-logo">
        <router-link class="logo logo-primary transform-scale-h" title="Logo" to="/">
            <img @click="closeModals" src="~/assets/img/logo/logo-dark.svg" alt="Logo">
        </router-link>
    </div>
</template>

<script>
    export default {
        name: 'HeaderLogo',
        props: [ 'logoColor' ],
                computed: {
            currentPage() {
                return this.$route.path;
            },
            showMenuModal () {
                return this.$store.state.showMenuModal
            },
            showSearchModal () {
                return this.$store.state.showSearchModal
            }
        },
        methods: {
            closeModals: function() {
                if (this.currentPage === '/') {
                    if (this.showSearchModal) {
                        const searchModal = document.getElementById('search-modal');
                        searchModal.classList.remove( 'show' );
                        setTimeout(() => this.$store.commit( 'closeSearchModal' ), 150 );
                    }
                    if (this.showMenuModal) {
                        this.$store.commit( 'closeMenuModal' );

                    }
                } else {
                    return;
                }
            }
        }
    }
</script>

<style scoped>
    .site-header .logo img {
        width: 6.6rem; /* 132px */
    }
</style>
