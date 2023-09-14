<template>
  <div id="contacts-index">
    <Loading />

    <Header logoColor='dark' />

    <main id="main" class="site-main">
      <div class="content">
        <div class="clearfix">
          <template v-if="Object.keys(containers).length">
          <PageTitle :title="containers.contactpage.cpagetitle" :description="containers.contactpage.cpagedesc"/>

          <section id="contacts" class="block spacer p-top-xl overflow-hidden">
            <div class="wrapper">
              <div class="contact-list-group">
                <div class="list-group list-group-horizontal">
                  <div class="list-group-item">
                    <h5 class="list-group-item-title">{{containers.contactpage.addrtitle}}</h5>
                    <p class="list-group-item-text">{{containers.contactpage.address}}</p>
                  </div>

                  <div class="list-group-item">
                    <h5 class="list-group-item-title">{{containers.contacts.conetitle}}</h5>
                    <p class="list-group-item-text"><a :href="`tel:+1${containers.contacts.contactOnePhone}`">+1{{containers.contacts.contactOnePhone}}</a><br><a :href="`mailto:${containers.contacts.contactOneMail}`">{{containers.contacts.contactOneMail}}</a></p>
                  </div>

                  <div class="list-group-item">
                    <h5 class="list-group-item-title">{{containers.contacts.csecondtitle}}</h5>
                    <p class="list-group-item-text"><a :href="`tel:+1${containers.contacts.contactTwoPhone}`">+1{{containers.contacts.contactTwoPhone}}</a><br><a :href="`mailto:${containers.contacts.contactTwoMail}`">{{containers.contacts.contactTwoMail}}</a></p>
                  </div>
                </div>
              </div>

              <div class="img-no-wrap-1 spacer p-top-xl">
                <div class="img object-fit">
                  <div class="object-fit-cover">
                    <img :src="$imageUrl(containers.contactpage.contactImage, 'md')" alt="Contacts">
                  </div>
                </div>
              </div>
            </div>
          </section>

            <section id="contact-form" class="block spacer p-top-xl">
              <div class="wrapper">
                <div class="title">
                  <h2>{{containers.contactpage.cformtitle}}</h2>
                </div>

                <div class="description">
                  <p>{{containers.contactpage.cformdescription}}</p>
                </div>

                <div class="spacer p-top-lg">
                  <ContactsForm />
                </div>
              </div>
            </section>
          </template>
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

import api from "../../mixins/api";

export default {
  mixins: [api],
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
    console.log(this.containers)
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
