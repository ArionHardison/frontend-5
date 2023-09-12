<template>
  <div id="service-inside-index">
    <Loading />

    <Header logoColor='dark' />

    <main id="main" class="site-main">
      <PageTitle />

      <div id="page-content" class="spacer p-top-xl">
        <div class="content">
          <div class="img-no-wrap-3">
            <div class="img object-fit">
              <div class="object-fit-cover">
                <img src="assets/img/placeholder/1920x631.jpg" alt="Services">
              </div>
            </div>
          </div>

          <div class="spacer p-top-xl">
            <div class="wrapper">
              <div class="row gutter-width-sm with-pb-md">
                <div class="col-sm-6 col-md-6 col-lg-6 col-xl-6">
                  <div class="description">
                    <h2>Location</h2>
                    <p>But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the.</p>
                  </div>
                </div>

                <div class="col-sm-6 col-md-6 col-lg-6 col-xl-6">
                  <div class="description">
                    <h2>Vision</h2>
                    <p>But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the.</p>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="spacer p-top-xl">
            <div class="wrapper">
              <router-link title="Back to Services" class="btn btn-lg btn-link btn-line line-active p-0 border-0 min-w-auto link-no-space spacer m-right-xs" to="/services">Back to Services</router-link>
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

import PageTitle from '~/components/blocks/service-inside/PageTitle';

export default {
  components: {
    Loading,
    Header,
    PageTitle,
    Footer
  },
  mounted: function() {
    document.body.classList.add( 'single-adveits_services' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'single-adveits_services' );
  },
  metaInfo: {
    title: 'Service inside | Olum - Business & Events Management Agency Vue JS Template',
    titleTemplate: '%s'
  }
}
</script>
