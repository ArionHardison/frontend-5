<template>
    <section id="services" class="block-2 spacer p-top-xl">
        <div class="wrapper">
            <div class="title">
                <h2>Our Services</h2>
            </div>
        </div>

        <div class="services">
            <div class="items clearfix">
                <nuxt-link v-for="program in programs.data" :key="program.id" class="item"  :to="`/program/${$slug(program.id, program.name)}`">
                    <div class="item-content">
                        <h4 class="item-title">{{ program.name }}</h4>
                    </div>

                    <div class="img object-fit">
                        <div class="object-fit-cover">
                            <img :src="$imageUrl('md', program.program_image, false)" :alt="program.name">
                        </div>
                    </div>

                    <div class="img-bg-color"></div>
                </nuxt-link>
            </div>
        </div>
    </section>
</template>

<script>
    import api from "../../../mixins/api";
    export default {
        name: 'services',
        mixins: [api],
        data() {
            return {
              programs: {
                data: []
              },
            }
        },
        async mounted() {
          this.programs = await this.get("public/get-recent-programs");
        },
    }
</script>
