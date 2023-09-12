<template>
  <div id="search-results-index">
    <Loading />

    <Header logoColor='dark'/>

    <main id="main" class="site-main">
      <PageTitle />

      <div id="page-content" class="spacer p-top-xl">
        <div class="wrapper">
          <div class="row gutter-width-sm with-pb-lg" id="results">
            <div v-for="searchItem in searchItems" :key="searchItem.id" class="col-xl-4 col-lg-4 col-md-6 col-sm-12">
              <div class="card border-0">
                <div class="card-body p-0">
                  <h4>
                    <router-link :title="searchItem.title" class="d-block" :to="searchItem.link">{{ searchItem.title }}</router-link>
                  </h4>

                  <p>
                    <router-link :title="searchItem.category" class="extra-bold" :to="searchItem.categoryLink">{{ searchItem.category }}</router-link>
                  </p>

                  <p>At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores.</p>
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

import PageTitle from '~/components/blocks/search-results/PageTitle';
import SearchItems from '~/data/search-results/searchItems.json';

export default {
  data() {
    return {
      searchItems: SearchItems.searchItems
    };
  },
  components: {
    Loading,
    Header,
    PageTitle,
    Footer
  },
  mounted: function() {
    document.body.classList.add( 'search-results' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'search-results' );
  },
  metaInfo: {
    title: 'Search results | Olum - Business & Events Management Agency Vue JS Template',
    titleTemplate: '%s'
  }
}
</script>
