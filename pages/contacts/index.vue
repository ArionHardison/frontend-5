<template>
  <div id="contacts-index">
    <Loading />

    <Header logoColor='dark' />

    <main id="main" class="site-main">
      <div class="content">
        <div class="clearfix">
          <PageTitle />

          <section id="contacts" class="block spacer p-top-xl overflow-hidden">
            <div class="wrapper">
              <div class="contact-list-group">
                <div class="list-group list-group-horizontal">
                  <div class="list-group-item">
                    <h5 class="list-group-item-title">Location</h5>
                    <p class="list-group-item-text">6 Bennett Drive, Sutton Coldfield, United Kingdom, B74 4BF</p>
                  </div>

                  <div class="list-group-item">
                    <h5 class="list-group-item-title">Manager</h5>
                    <p class="list-group-item-text"><a href="tel:+43253312523">+432 533 12 523</a><br><a href="mailto:info@company.com">info@company.com</a></p>
                  </div>

                  <div class="list-group-item">
                    <h5 class="list-group-item-title">CEO</h5>
                    <p class="list-group-item-text"><a href="tel:+43253312523">+432 533 12 523</a><br><a href="mailto:info@company.com">info@company.com</a></p>
                  </div>
                </div>
              </div>

              <div class="img-no-wrap-1 spacer p-top-xl">
                <div class="img object-fit">
                  <div class="object-fit-cover">
                    <img src="assets/img/placeholder/1487x631.jpg" alt="Contacts">
                  </div>
                </div>
              </div>
            </div>
          </section>

          <section id="contact-form" class="block spacer p-top-xl">
            <div class="wrapper">
              <div class="title">
                <h2>Write us here</h2>
              </div>

              <div class="description">
                <p>But I must explain to you how all this mistaken.</p>
              </div>

              <div class="spacer p-top-lg">
                <ContactsForm />
              </div>
            </div>
          </section>
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

import PageTitle from '~/components/blocks/contacts/PageTitle';
import ContactsForm from '~/components/Forms/ContactsForm';

export default {
  components: {
    Loading,
    Header,
    PageTitle,
    ContactsForm,
    Footer
  },
  data(){
    return {
      containers: {}
    }
  },
  async created() {
    const containers = await this.get("public/get-containers/contacts|cformitems|contactpage")

    let sortedContainers = {};
    if(containers) {
      for (let container of containers) {
        sortedContainers[container.container_call] = container;
      }
    }
    this.containers = sortedContainers;
  },
  mounted: function() {
    document.body.classList.add( 'page' );
  },
  beforeDestroy() {
    document.body.classList.remove( 'page' );
  },
  metaInfo: {
    title: 'Contacts | Olum - Business & Events Management Agency Vue JS Template',
    titleTemplate: '%s'
  }
}
</script>
