<template>
  <div id="news-index">
    <Loading />

    <Header logoColor='dark'/>

    <main id="main" class="site-main">
      <PageTitle />

      <div id="page-content" class="spacer p-top-xl">
        <div class="wrapper">
          <div class="content">
            <div id="blog">
              <div class="row gutter-width-sm">
                <div class="col-md-12 col-lg-4 col-xl-4 order-1 order-lg-0 order-xl-0">
                  <Sidebar />
                </div>

                <div class="col-xl-8 col-lg-8  col-md-12 order-0 order-lg-1 order-xl-1 style-default">
                  <NewsBlog />
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

import PageTitle from '~/components/blocks/news/PageTitle';
import Sidebar from '~/components/blocks/news/Sidebar';
import NewsBlog from '~/components/blocks/news/Blog';

export default {
  components: {
    Loading,
    Header,
    PageTitle,
    Sidebar,
    NewsBlog,
    Footer
  },
  mounted: function() {
    document.body.classList.add( 'blog' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'blog' );
  },
  metaInfo: {
    title: 'News | Olum - Business & Events Management Agency Vue JS Template',
    titleTemplate: '%s'
  }
}
</script>
