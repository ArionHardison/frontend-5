<template>
    <div id="about-index">
        <Loading />

        <Header />
        
        <main id="main" class="site-main">
            <PageTitle />

            <div id="page-content" class="spacer p-top-xl">
                <div class="wrapper">
                    <div class="content">
                        <div class="clearfix">
                            <div id="about-us-img" class="block">
                                <div class="about-img">
                                    <div class="img object-fit">
                                        <div class="object-fit-cover">
                                            <img src="assets/img/placeholder/1600x700.jpg" alt="About us">
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div id="about-us" class="block spacer p-top-xl">
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

                            <OurTeam />

                            <Testimonials />

                            <div id="services" class="block spacer p-top-xl">
                                <div class="text-center">
                                    <router-link to="/services" class="btn btn-outline-secondary">See our Services</router-link>
                                </div>
                            </div>

                            <Clients />
                        </div>
                    </div>
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

    import PageTitle from '../../blocks/about/PageTitle';
    import OurTeam from '../../blocks/about/OurTeam';
    import Testimonials from '../../blocks/about/Testimonials';
    import Clients from '../../blocks/about/Clients';

    export default {
        components: {
            Loading,
            Header,
            PageTitle,
            OurTeam,
            Testimonials,
            Clients,
            Footer
        },
        mounted: function() {
            document.body.classList.add( 'page' );
        },
        beforeDestroy() {
            document.body.classList.remove( 'page' );
        },
        metaInfo: {
            title: 'About | Mykery - Beauty Salon Vue JS Template',
            titleTemplate: '%s'
        }
    }
</script>
