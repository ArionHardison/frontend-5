<template>
  <fragment>
    <transition
        @enter="startTransitionModal"
        @after-enter="endTransitionModal"
        @before-leave="endTransitionModalLeave"
        @after-leave="startTransitionModalLeave"
    >
      <div
          v-show="showSearchModal"
          class="modal fade"
          id="search-modal"
          tabindex="-1"
          role="dialog"
          aria-labelledby="search-modal"
          aria-hidden="true"
          ref="modal"
      >
        <div class="modal-dialog modal-full" role="document">
          <div class="wrapper">
            <div class="modal-content">
              <div class="modal-header modal-header-top">
                <div
                    class="header-content d-flex justify-content-between w-100"
                >
                  <div class="header-left align-self-center">
                    <div class="d-flex align-items-center">
                      <Logo :light="true"/>
                    </div>
                  </div>

                  <div class="header-right d-flex justify-content-end">
                    <div class="d-flex align-items-center">
                      <div class="search-close-toggle">
                        <button
                            @click="closeModal"
                            type="button"
                            class="btn btn-primary btn-square min-w-auto"
                            data-dismiss="modal"
                            aria-label="Close"
                        >
                          <i class="fas fa-times i-default"></i>
                        </button>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <div class="modal-body modal-body-centered">
                <SearchForm redirect path="/programs" @search="closeModal"/>
              </div>

              <div class="modal-footer">
                <div
                    class="d-flex flex-column flex-md-row flex-lg-row flex-xl-row justify-content-between w-100"
                >
                  <div class="modal-text">
                    <p>
                      © {{ new Date().getFullYear() }}  {{copyRight}}
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </transition>

    <div class="modal-backdrop fade d-none" ref="backdrop"></div>
  </fragment>
</template>

<script>
import { Fragment } from "vue-fragment";
import { mapMutations } from "vuex";

import Logo from "~/components/blocks/header/HeaderLogo";
import SearchForm from "../Forms/SearchForm";

export default {
  name: "Search-Modal",
  components: {
    Logo,
    SearchForm,
    Fragment,
  },
  computed: {
    showSearchModal() {
      return this.$store.state.showSearchModal;
    },
    copyRight(){
      return this.$store.state.layout.items.copy
    },
  },
  methods: {
    ...mapMutations(["toggleSearchModal"]),
    closeModal() {
      if(process.client && document.getElementById("search-modal")) {
        document.getElementById("search-modal").classList.remove("show");

        setTimeout(() => this.$store.commit("closeSearchModal"), 150);
      }
    },
    startTransitionModal() {
      if(process.client && this.$refs.backdrop) {
        if (!this.$refs.backdrop.classList.contains("d-block")) {
          this.$refs.backdrop.classList.add("d-block");
        }

        if (!this.$refs.modal.classList.contains("d-block")) {
          this.$refs.modal.classList.add("d-block");
        }
      }
    },
    startTransitionModalLeave() {
      if(process.client && this.$refs.backdrop) {
        if (this.$refs.backdrop.classList.contains("d-block")) {
          this.$refs.backdrop.classList.remove("d-block");
        }

        if (this.$refs.modal.classList.contains("show")) {
          this.$refs.modal.classList.remove("show");
        }
      }
    },
    endTransitionModal() {
      if(process.client && this.$refs.backdrop) {
        if (!this.$refs.backdrop.classList.contains("show")) {
          this.$refs.backdrop.classList.add("show");
        }

        if (!this.$refs.modal.classList.contains("show")) {
          this.$refs.modal.classList.add("show");
        }
        if (process.client) {
          if (!document.body.classList.contains("modal-open")) {
            document.body.classList.add("modal-open");
          }
        }
      }
    },
    endTransitionModalLeave() {
      if(process.client && this.$refs.backdrop) {
        if (this.$refs.backdrop.classList.contains("show")) {
          this.$refs.backdrop.classList.remove("show");
        }
        if (process.client) {
          if (document.body.classList.contains("modal-open")) {
            if (
                !document.getElementById("menu-modal").classList.contains("d-block")
            ) {
              document.body.classList.remove("modal-open");
            }
          }
        }

        if (this.$refs.modal.classList.contains("d-block")) {
          this.$refs.modal.classList.remove("d-block");
        }

        if (this.$refs.backdrop.classList.contains("d-block")) {
          this.$refs.backdrop.classList.remove("d-block");
        }
      }
    },
  },
  mounted() {
    if (process.client) {
      document.addEventListener("keydown", (e) => {
        if (e.isComposing || e.keyCode === 27) {
          this.closeModal();
        }
      });
    }
  },
  beforeDestroy() {
    if (process.client) {
      if (document.body.classList.contains("modal-open")) {
        document.body.classList.remove("modal-open");
      }

      document.removeEventListener("keydown", (e) => {
        if (e.isComposing || e.keyCode === 27) {
          this.closeModal();
        }
      });
    }
    this.$store.commit("variablesNull");
  },
};
</script>
