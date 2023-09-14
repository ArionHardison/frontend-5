<template>
    <fragment>
        <transition @enter="startTransitionModal" @after-enter="endTransitionModal" @before-leave="endTransitionModalLeave" @after-leave="startTransitionModalLeave">
            <div v-show="showMenuModal" ref="modal" class="modal fade" id="menu-modal" tabindex="-1" role="dialog" aria-labelledby="menu-modal" aria-hidden="true">
                <div class="modal-dialog modal-full h-100" role="document">
                    <div class="wrapper h-100">
                        <div class="modal-content h-100">
                            <div class="modal-header modal-header-top">
                                <Logo :light="true" />

                                <button @click="toggleMenuModal" type="button" class="close btn btn-link border-0 min-w-auto transform-scale-h" data-dismiss="modal" aria-label="Close">
                                    <span class="adveits-i adv-close">
                                        <span></span>
                                        <span></span>
                                    </span>
                                </button>
                            </div>

                            <div class="modal-body d-flex justify-content-between">
                                <div class="align-self-start">
                                    <SearchModalButton />
                                </div>

                                <div class="align-self-center animated fadeinright">
                                    <ModalMenuPrimary />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </transition>

        <div class="modal-backdrop fade d-none" ref="backdrop"></div>
    </fragment>
</template>

<script>
    import { Fragment } from 'vue-fragment'
    import { mapMutations } from 'vuex';

    import SearchModalButton from '~/components/Button/SearchModalButton';
    import Logo from '~/components/blocks/header/HeaderLogo';
    import ModalMenuPrimary from '~/components/blocks/General/ModalMenuPrimary';

    export default {
        name: 'Menu-Modal',
        components: {
            SearchModalButton,
            Logo,
            ModalMenuPrimary,
            Fragment
        },
        computed: {
            showMenuModal () {
                return this.$store.state.showMenuModal
            }
        },
        methods: {
            ...mapMutations([
                'toggleMenuModal'
            ]),
            startTransitionModal() {
                if ( ! this.$refs.backdrop.classList.contains( 'd-block' ) ) {
                    this.$refs.backdrop.classList.add( 'd-block' );
                }

                if ( ! this.$refs.modal.classList.contains( 'd-block' ) ) {
                    this.$refs.modal.classList.add( 'd-block' );
                }
            },
            startTransitionModalLeave() {
                if ( this.$refs.backdrop.classList.contains( 'd-block' ) ) {
                    this.$refs.backdrop.classList.remove( 'd-block' );
                }

                if ( this.$refs.modal.classList.contains( 'd-block' ) ) {
                    this.$refs.modal.classList.remove( 'd-block' );
                }
            },
            endTransitionModal() {
                if ( ! this.$refs.backdrop.classList.contains( 'show' ) ) {
                    this.$refs.backdrop.classList.add( 'show' );
                }

                if ( ! this.$refs.modal.classList.contains( 'show' ) ) {
                    this.$refs.modal.classList.add( 'show' );
                }

                if ( ! document.body.classList.contains( 'modal-open' ) ) {
                    document.body.classList.add( 'modal-open' )
                }
            },
            endTransitionModalLeave() {
                if ( this.$refs.backdrop.classList.contains( 'show' ) ) {
                    this.$refs.backdrop.classList.remove( 'show' );
                }

                if ( this.$refs.modal.classList.contains( 'show' ) ) {
                    this.$refs.modal.classList.remove( 'show' );
                }

                if ( document.body.classList.contains( 'modal-open' ) ) {
                    document.body.classList.remove( 'modal-open' )
                }
            }
        },
        mounted() {
            document.addEventListener( 'keydown', e => {
                if ( document.getElementById( 'search-modal' ).classList.contains( 'd-block' ) ) {
                    return;
                } else if ( e.isComposing || e.keyCode === 27 ) {
                    this.$store.commit( 'closeMenuModal' );
                }
            });
        },
        beforeDestroy() {
            if ( document.body.classList.contains( 'modal-open' ) ) {
                document.body.classList.remove( 'modal-open' )
            }

            document.removeEventListener( 'keydown', e => {
                if ( e.isComposing || e.keyCode === 27 ) {
                    this.$store.commit( 'closeMenuModal' );
                }
            });

            this.$store.commit( 'variablesNull' );
        }
    }
</script>

<style scoped>
    #menu-modal .modal-header .logo img {
        width: 6.6rem; /* 132px */
    }
</style>
