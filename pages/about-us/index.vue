<template>
  <div id="about-us-index">
    <Loading />

    <Header logoColor='dark' />

    <main id="main" class="site-main">
      <PageTitle />

      <div id="page-content" class="spacer p-top-xl">
        <div class="content">
          <div class="clearfix">
            <AboutUs />

            <Team />
          </div>
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

import PageTitle from '~/components/blocks/about-us/PageTitle';
import AboutUs from '~/components/blocks/about-us/Abouts-us';
import Team from '~/components/blocks/about-us/Team'

export default {
  components: {
    Loading,
    Header,
    PageTitle,
    AboutUs,
    Team,
    Footer
  },
  mounted: function() {
    document.body.classList.add( 'page' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'page' );
  },
  metaInfo: {
    title: 'About Us | Olum - Business & Events Management Agency Vue JS Template',
    titleTemplate: '%s'
  }
}
</script>
