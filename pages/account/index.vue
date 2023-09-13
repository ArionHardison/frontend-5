<template>
  <div id="news-single-post-index">
    <Loading />

    <Header logoColor='dark'/>

    <main id="main" class="site-main">
      <PageTitle title="My Account"/>

      <div id="page-content" class="spacer p-top-xl">
        <div class="wrapper">
          <div class="content">
            <div id="single">
              <div class="row gutter-width-sm">
                <div class="col-lg-12">

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
import api from "../../mixins/api";
export default {
  mixins: [api],
  components: {
    Loading,
    Header,
    PageTitle,
    Footer
  },
  data() {
    return {
      programs: [],
      userData: null,
      tasks: [],
    }
  },
  middleware: "user",
  async created() {
    this.programs = await this.get("personal-chain");
    this.userData = await this.get("user/get-data");
    await this.getTasks();
  },
  methods: {
    async getTasks() {
      const data = await this.get("personal-chain/tasks");
      if(data){
        this.tasks = data;
      }
    },
  },
  mounted: function() {
    document.body.classList.add( 'single-post' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'single-post' );
  },
  metaInfo: {
    title: 'My Account',
    titleTemplate: '%s'
  }
}
</script>
