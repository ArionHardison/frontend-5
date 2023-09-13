<template>
  <div id="home-index">
    <Loading />

    <Header logoColor='dark' />

    <main id="main" class="site-main">
      <div class="content">
        <div class="clearfix">
          <PageTitle />

          <AboutUs />

          <Services />

          <Partners />
        </div>
      </div>
    </main>

    <Footer />
  </div>
</template>

<script>
import Loading from '~/components/Loading/Loading';
import Header from '~/components/blocks/header/Header';
import Footer from '~/components/blocks/footer/Footer';

import PageTitle from '~/components/blocks/index/PageTitle';
import AboutUs from '~/components/blocks/index/About-us';
import Services from '~/components/blocks/index/Services';
import Partners from '~/components/blocks/index/Partners';
import api from "../mixins/api";
export default {
  mixins: [api],
  components: {
    Loading,
    Header,
    PageTitle,
    AboutUs,
    Services,
    Partners,
    Footer
  },
  data() {
    return {
      entities: {}
    }
  },
  async created() {
    const entities = await this.get(`public/get-entities/home`)
    let sortedEntities = {};
    if(entities) {
      for (let entity of entities) {
        sortedEntities[entity.entity_call] = entity;
      }
    }
    this.entities = sortedEntities;
  },
  mounted: function() {
    document.body.classList.add( 'home' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'home' );
  },
  metaInfo: {
    title: 'Home | Olum - Business & Events Management Agency Vue JS Template',
    titleTemplate: '%s'
  }
}
</script>
