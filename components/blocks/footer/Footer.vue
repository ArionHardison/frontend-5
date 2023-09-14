<template>
    <fragment>
        <footer id="footer" class="site-footer">
            <div class="wrapper">
                <div class="d-flex flex-column flex-lg-row flex-xl-row justify-content-between">
                    <div v-if="currentPage !== '/404'" class="logo logo-secondary">
                        <img :src="logo" alt="Logo">
                    </div>
                    <template v-if="Object.keys(entities).length">
                      <div class="footer-widgets">
                          <div class="footer-widget-area d-flex flex-wrap justify-content-lg-end justify-content-xl-end">
                              <div class="widget widget_text">
                                  <h6 class="widget-title">{{entities.footer.contacts.conetitle}}</h6>

                                  <div class="textwidget">
                                      <p><a :href="`tel:+1${entities.footer.contacts.contactOnePhone}`">+1{{entities.footer.contacts.contactOnePhone}}</a></p>
                                      <p><a :href="`mailto:${entities.footer.contacts.contactOneMail}`">{{entities.footer.contacts.contactOneMail}}</a></p>
                                  </div>
                              </div>

                              <div class="widget widget_text">
                                <h6 class="widget-title">{{entities.footer.contacts.csecondtitle}}</h6>

                                  <div class="textwidget">
                                    <p><a :href="`tel:+1${entities.footer.contacts.contactTwoPhone}`">+1{{entities.footer.contacts.contactTwoPhone}}</a></p>
                                    <p><a :href="`mailto:${entities.footer.contacts.contactTwoMail}`">{{entities.footer.contacts.contactTwoMail}}</a></p>
                                  </div>
                              </div>
                          </div>
                      </div>
                    </template>
                </div>

                <div class="footer">
                    <div class="d-flex flex-column flex-lg-row flex-xl-row justify-content-between">
                        <div class="align-self-center">
                            <div class="copyright">
                                <p>© {{ new Date().getFullYear() }} {{copyright}}</p>
                            </div>
                        </div>
                        <template v-if="Object.keys(entities).length">
                          <div class="align-self-center">
                              <FooterMenuSecondary :facebook="entities.footer.contacts.facebookLink" :linked="entities.footer.contacts.linkedinLink"/>
                          </div>
                        </template>
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
    import api from "../../../mixins/api";
    export default {
        name: 'Footer',
        mixins: [api],
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
            },
            logo(){
              return this.$imageUrl(this.$store.state.layout.items.logoLight, 'tb');
            },
            copyright(){
              return this.$store.state.layout.items.copy;
            },
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
          console.log(this.entities);
        }
    }
</script>

<style scoped>
    .site-footer .logo img {
        width: 11rem; /* 220px */
    }
</style>
