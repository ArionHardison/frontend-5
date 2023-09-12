<template>
  <div id="services-index">
    <Loading />

    <Header logoColor='dark' />

    <main id="main" class="site-main pb-0">
      <PageTitle />

      <div id="page-content" class="spacer p-top-xl">
        <div class="content">
          <Services />

          <section id="we-guarantee" class="block spacer p-top-xl">
            <div class="wrapper">
              <div class="title">
                <h2>We guarantee</h2>
              </div>

              <div class="description max-width-1">
                <p>But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the.</p>
              </div>
            </div>
          </section>

          <div class="spacer p-top-xl">
            <div class="img-no-wrap-3">
              <div class="img object-fit">
                <div class="object-fit-cover">
                  <img src="assets/img/placeholder/1920x631.jpg" alt="Services">
                </div>
              </div>
            </div>
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

import PageTitle from '~/components/blocks/services/PageTitle';
import Services from '~/components/blocks/services/ServicesList';

export default {
  components: {
    Loading,
    Header,
    PageTitle,
    Services,
    Footer
  },

  mounted: function() {
    document.body.classList.add( 'archive' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'archive' );
  },
  metaInfo: {
    title: 'Services | Olum - Business & Events Management Agency JS Template',
    titleTemplate: '%s'
  }
}
</script>
