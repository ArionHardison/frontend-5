<template>
  <div id="news-single-post-index">
    <Loading />

    <Header logoColor='dark'/>

    <main id="main" class="site-main">
      <PageTitle title="Sign Up"/>

      <div id="page-content" class="spacer p-top-xl">
        <div class="wrapper">
          <div class="content">
            <div id="single">
              <div class="row gutter-width-sm">
                <div class="col-lg-6 offset-lg-3 col-md-8 offset-md-2 col-xl-4 offset-xl-4 col-12">
                    <SignUpForm/>
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
import SignUpForm from "../../components/Forms/SignUpForm";
import PageTitle from '~/components/PageTitle';

export default {
  components: {
    Loading,
    Header,
    SignUpForm,
    PageTitle,
    Footer
  },
  mounted: function() {
    document.body.classList.add( 'single-post' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'single-post' );
  },
  metaInfo: {
    title: 'Sign Up',
    titleTemplate: '%s'
  }
}
</script>
