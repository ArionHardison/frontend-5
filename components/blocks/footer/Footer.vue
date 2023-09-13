<template>
    <fragment>
        <footer id="footer" class="site-footer">
            <div class="wrapper">
                <div class="d-flex flex-column flex-lg-row flex-xl-row justify-content-between">
                    <div v-if="currentPage !== '/404'" class="logo logo-secondary">
                        <img src="~assets/img/logo/logo-light.svg" alt="Logo">
                    </div>

                    <div class="footer-widgets">
                        <div class="footer-widget-area d-flex flex-wrap justify-content-lg-end justify-content-xl-end">
                            <div class="widget widget_text">
                                <h6 class="widget-title">Manager</h6>

                                <div class="textwidget">
                                    <p><a href="tel:+43253312523">+432 533 12 523</a></p>
                                    <p><a href="mailto:info@company.com">info@company.com</a></p>
                                </div>
                            </div>

                            <div class="widget widget_text">
                                <h6 class="widget-title">CEO</h6>

                                <div class="textwidget">
                                    <p><a href="tel:+43253312523">+432 533 12 523</a></p>
                                    <p><a href="mailto:info@company.com">info@company.com</a></p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="footer">
                    <div class="d-flex flex-column flex-lg-row flex-xl-row justify-content-between">
                        <div class="align-self-center">
                            <div class="copyright">
                                <p>© {{ new Date().getFullYear() }} Business & Events Management Agency Vue JS Template by <a href="https://www.adveits.com">Adveits</a></p>
                            </div>
                        </div>

                        <div class="align-self-center">
                            <FooterMenuSecondary />
                        </div>
                    </div>
                </div>
            </div>
        </footer>

        <div id="modals">
            <MenuModal />

            <SearchModal />
        </div>
    </fragment>
</template>

<script>
    import { Fragment } from 'vue-fragment';

    import FooterMenuSecondary from './FooterMenuSecondary';
    import MenuModal from '~/components/Modal/MenuModal';
    import SearchModal from '~/components/Modal/SearchModal';

    export default {
        name: 'Footer',
        components: {
            Fragment,
            MenuModal,
            SearchModal,
            FooterMenuSecondary
        },
        data() {
          return {
            entities: {}
          }
        },
        computed: {
            currentPage() {
                return this.$route.path;
            }
        },
        async created(){
          const entities = await this.get(`public/get-entities/footer`)
          let sortedEntities = {};
          if(entities) {
            for (let entity of entities) {
              sortedEntities[entity.entity_call] = entity;
            }
          }
          this.entities = sortedEntities;
        }
    }
</script>

<style scoped>
    .site-footer .logo img {
        width: 11rem; /* 220px */
    }
</style>
