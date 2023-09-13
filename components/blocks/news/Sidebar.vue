<template>
  <aside id="aside" class="widget-area">
    <template v-if="program!==null">
      <div class="text-center">
        <Avatar :src="program.author.profile_picture" width="50" height="50"/>
        <div class="col-12 mt-2 mb-2">
          <b class="mt-2 mb-2">{{program.author.full_name}}</b><br/>
          {{program.author.roles.toString()}}
        </div>
      </div>
      <template v-if="accessToken">
        <template v-if="program.access_type === 1">
          <h3>Free</h3>
          <button
              class="
                  btn btn-1 btn-primary btn-block
                  mt-4
                  mb-4
                  text-white
                  "
              type="button"
              :disabled="program.borken"
              @click="startProgram"
          >
            Start Program
          </button>
        </template>
        <template v-else>
          <h3>
            {{ program.sale.amount / 100 }}
            <small>USD</small>
          </h3>
          <button
              :disabled="program.borken"
              class="
                  btn btn-1 btn-primary btn-block
                  mt-4
                  text-white
                  mb-4
                  "
              type="button"
              @click="startProgram"
          >
            Buy Program
          </button>
        </template>
      </template>
      <template v-else>
        You should have account to start program
        <nuxt-link to="/auth/login" class="btn btn-1 btn-primary btn-block mt-2 mb-2">Sign In</nuxt-link>
      </template>
    </template>
    <div class="widget widget_search">
      <SearchForm />
    </div>
    <ProgramCategories />
    <TagCloud />
  </aside>
</template>
<script>
import SearchForm from '~/components/Forms/SearchForm';
import ProgramCategories from '~/components/blocks/sidebar/ProgramCategories';
import TagCloud from '~/components/blocks/sidebar/TagCloud';
import Avatar from "~/components/ui/Avatar.vue";
import api from "~/mixins/api";
export default {
  mixins: [api],
  props: {
    program: {
      type: Object,
      default: () =>{
        return null;
      }
    }
  },
  computed: {
    accessToken(){
      return this.$store.state.authData.accessToken;
    }
  },
  name: 'Sidebar',
  components: {
    SearchForm,
    ProgramCategories,
    TagCloud,
    Avatar
  },
  methods: {
    async startProgram() {
      const program = await this.post(`program-sale/buy`, {
        program_id: this.program.id,
      });
      if (program) {
        if (this.program.access_type === 1) {
          await this.$router.push({name: "account"});
        } else {
          if (process.client) {
            window.location.href = program.url;
          }
        }
      }
    },
  }
}
</script>