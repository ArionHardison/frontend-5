<template>
    <div id="home-index">
        <Loading />

        <Header />

        <main id="main" class="site-main content-no-spacing">
            <div class="content">
                <div class="clearfix">
                    <PageTitle />

                    <section id="contact-us" class="block">
                        <div class="bg-pink-light spacer p-top-xl p-bottom-xl">
                            <div class="wrapper text-center">
                                <div class="title">
                                    <h2>You can contact us</h2>
                                </div>

                                <router-link to="/contacts" class="btn btn-outline-secondary">Contact</router-link>
                            </div>
                        </div>
                    </section>

                    <Services />

                    <section id="about-us" class="block spacer p-top-xl">
                        <div class="wrapper">
                            <div class="row gutter-width-sm">
                                <div class="col-xl-8 col-lg-8 col-md-12 col-sm-12">
                                    <div class="title">
                                        <h2>We are born in Europe, raised in New York. Mykery creates luxurious makeup and hairstyles that is easy to take care of everyday.</h2>
                                    </div>
                                </div>
                            </div>

                            <div class="row gutter-width-sm justify-content-end">
                                <div class="col-xl-5 col-lg-5 col-md-12 col-sm-12">
                                    <div class="description">
                                        <p>Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock.</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>

                    <div id="img" class="block spacer p-top-xl">
                        <div class="img-no-wrap-1 img-gray">
                            <div class="img object-fit">
                                <div class="object-fit-cover">
                                    <img src="assets/img/placeholder/1920x700.jpg" alt="Beauty Salon">
                                </div>
                            </div>
                        </div>
                    </div>

                    <News />

                    <NewsLetter />
                </div>
            </div>
        </main>
    
        <Footer />
    </div>
</template>

<script>
    import Loading from '../../components/Loading/Loading';
    import Header from '../../blocks/header/Header';
    import Footer from '../../blocks/footer/Footer';

    import PageTitle from '../../blocks/index/PageTitle';
    import Services from '../../blocks/index/Services';
    import News from '../../blocks/index/News';
    import NewsLetter from '../../blocks/index/NewsLetter';

    export default {
        components: {
            Loading,
            Header,
            PageTitle,
            Services,
            News,
            NewsLetter,
            Footer
        },
        mounted: function() {
            document.body.classList.add( 'home' );
            document.body.classList.add( 'header-absolute-true' );
        },
        beforeDestroy() {
            document.body.classList.remove( 'home' );
            document.body.classList.remove( 'header-absolute-true' );
        },
        metaInfo: {
            title: 'Home | Mykery - Beauty Salon Vue JS Template',
            titleTemplate: '%s'
        }
    }
</script>

<style scoped>
    #page-title {
        background-image: url('~@/assets/img/placeholder/1920x860.jpg');
    }
</style>
