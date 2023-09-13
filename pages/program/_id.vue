<template>
  <div id="news-single-post-index">
    <Loading />

    <Header logoColor='dark'/>

    <main id="main" class="site-main">
      <PageTitle :title="program.name" />

      <div id="page-content" class="spacer p-top-xl">
        <div class="wrapper">
          <div class="content">
            <div id="single">
              <div class="row gutter-width-sm">
                <div class="col-md-12 col-lg-4 col-xl-4 order-1 order-lg-0 order-xl-0">
                  <Sidebar :program="program"/>
                </div>

                <div class="col-xl-8 col-lg-8  col-md-12 order-0 order-lg-1 order-xl-1 single-content">
                  <div class="img object-fit">
                    <div class="object-fit-cover">
                      <img :src="$imageUrl(program.program_image, 'lg', false)" :alt="program.name">
                    </div>
                  </div>

                  <Meta :program="program"/>

                  <Description :description="program.description"/>

                  <Tags :tags="program.tags"/>

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

import PageTitle from '~/components/PageTitle';
import Sidebar from '~/components/blocks/news/Sidebar';
import Meta from '~/components/blocks/news-single-post/Meta';
import Description from '~/components/blocks/news-single-post/Description';
import Tags from '~/components/blocks/news-single-post/Tags';
export default {
  components: {
    Loading,
    Header,
    PageTitle,
    Sidebar,
    Meta,
    Description,
    Tags,
    Footer
  },
  data(){
    return {
      program: null,
    }
  },
  mounted: function() {
    document.body.classList.add( 'single-post' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'single-post' );
  },
  metaInfo: {
    title: 'Program',
    titleTemplate: '%s'
  }
}
</script>
