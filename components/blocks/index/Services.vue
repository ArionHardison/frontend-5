<template>
    <section id="services" class="block-2 spacer p-top-xl">
        <div class="wrapper">
            <div class="title">
                <h2>Programs</h2>
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
                            <img :src="$imageUrl(program.program_image, 'md', false)" :alt="program.name">
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
          let programs = await this.get("public/get-recent-programs");
          this.programs.data = this.getRandomElements(programs.data, 4)
        },
        methods: {
          getRandomElements(arr, n) {
            let tempArr = arr.slice();
            for (let i = tempArr.length - 1; i > 0; i--) {
              let j = Math.floor(Math.random() * (i + 1));
              [tempArr[i], tempArr[j]] = [tempArr[j], tempArr[i]];
            }
            return tempArr.slice(0, n);
          }
        }
    }
</script>
