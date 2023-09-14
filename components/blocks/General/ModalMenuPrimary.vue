<template>
    <nav class="menu-primary">
        <ul class="nav flex-column">
            <li @click="closeOnSameRoute" :class="[( currentPage === '/' ) ? activeClass : '', 'nav-item']">
                <router-link title="Home" to="/">Home</router-link>
            </li>

            <li @click="closeOnSameRoute" :class="[currentPage.includes('programs') || currentPage.includes('service-inside') ? activeClass : '', 'nav-item']">
                <router-link title="Services" to="/programs">Programs</router-link>
            </li>

            <li @click="closeOnSameRoute" :class="[currentPage.includes('contacts') ? activeClass : '', 'nav-item']">
                <router-link title="Contacts" to="/contacts">Contacts</router-link>
            </li>
            <template v-if="isGuest">
              <li @click="closeOnSameRoute" :class="[currentPage.includes('sign-in') ? activeClass : '', 'nav-item']">
                <router-link title="Sign In" to="/sign-in">Sign In</router-link>
              </li>
              <li @click="closeOnSameRoute" :class="[currentPage.includes('sign-up')  ? activeClass : '', 'nav-item']">
                <router-link title="Sign Up" to="/sign-up">Sign Up</router-link>
              </li>
            </template>
            <template v-else>
              <li @click="closeOnSameRoute" class="nav-item">
                <a href="javascript:void(0)" title="Clinic" @click="getClinicLink">Clinic</a>
              </li>
              <li @click="closeOnSameRoute" :class="[currentPage.includes('account') ? activeClass : '', 'nav-item']">
                <router-link title="My Account" to="/account">My Account</router-link>
              </li>
              <li @click="closeOnSameRoute" class="nav-item">
                <a href="javascript:void(0)" title="Sign Out" @click="signOut">Sign Out</a>
              </li>
            </template>
        </ul>
    </nav>
</template>

<script>
    import api from "../../../mixins/api";
    export default {
        mixins: [api],
        name: 'ModalMenuPrimary',
        data() {
            return {
                activeClass: 'current-nav-item'
            }
        },
        methods: {
            async getClinicLink(){
              if (process.browser) {
                if (this.isLoggedIn) {
                  const tokenData = await this.get("user/get-token");
                  window.location.href = `https://clinic.${window.location.hostname}?token=${tokenData.token}`;
                } else {
                  window.location.href = `https://clinic.${window.location.hostname}`;
                }
              }
            },
            async signOut() {
              await this.get(`user/sign-out`);
              this.$store.commit("signOut");
            },
            closeOnSameRoute: function( event ) {
                const clickTargetHref = event.target.getAttribute( 'href' );

                if ( clickTargetHref === this.$route.path ) {
                    this.toggleMenuModal();
                }
            },
            toggleMenuModal: function( event ) {
                this.$store.commit( 'toggleMenuModal' );
                this.$store.commit( 'variablesNull' );
            }
        },
        computed: {
            isGuest() {
              return this.$store.state.authData.accessToken === null;
            },
            isLoggedIn(){
              return this.$store.state.authData.accessToken;
            },
            currentPage() {
                return this.$route.path;
            }
        }
    }
</script>
