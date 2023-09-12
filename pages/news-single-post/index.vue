<template>
  <div id="news-single-post-index">
    <Loading />

    <Header logoColor='dark'/>

    <main id="main" class="site-main">
      <PageTitle />

      <div id="page-content" class="spacer p-top-xl">
        <div class="wrapper">
          <div class="content">
            <div id="single">
              <div class="row gutter-width-sm">
                <div class="col-md-12 col-lg-4 col-xl-4 order-1 order-lg-0 order-xl-0">
                  <Sidebar />
                </div>

                <div class="col-xl-8 col-lg-8  col-md-12 order-0 order-lg-1 order-xl-1 single-content">
                  <div class="img object-fit">
                    <div class="object-fit-cover">
                      <img src="assets/img/placeholder/1050x500.jpg" alt="Neque porro quisquam est qui dolorem at vero do">
                    </div>
                  </div>

                  <Meta />

                  <Description />

                  <Tags />

                  <Comments />
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

import PageTitle from '~/components/blocks/news-single-post/PageTitle';
import Sidebar from '~/components/blocks/news/Sidebar';
import Meta from '~/components/blocks/news-single-post/Meta';
import Description from '~/components/blocks/news-single-post/Description';
import Tags from '~/components/blocks/news-single-post/Tags';
import Comments from '~/components/blocks/news-single-post/Comments';

export default {
  components: {
    Loading,
    Header,
    PageTitle,
    Sidebar,
    Meta,
    Description,
    Tags,
    Comments,
    Footer
  },
  mounted: function() {
    document.body.classList.add( 'single-post' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'single-post' );
  },
  metaInfo: {
    title: 'News single post | Olum - Business & Events Management Agency Vue JS Template',
    titleTemplate: '%s'
  }
}
</script>
