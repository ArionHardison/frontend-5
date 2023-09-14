<template>
    <section id="about-us" class="block spacer p-top-xl overflow-hidden">
        <div class="wrapper">
            <div class="about-content-primary">
                <div class="img-no-wrap-1">
                    <div class="img object-fit">
                        <div class="object-fit-cover">
                            <img :src="$imageUrl(content.timage, 'md')" :alt="content.topTitle">
                        </div>
                    </div>
                </div>

                <div class="spacer m-top-xl">
                    <div class="title">
                        <h2>{{content.topTitle}}</h2>
                    </div>

                    <div class="description max-width-1">
                        <p>{{content.topDescription}}</p>
                    </div>
                </div>
            </div>

            <div class="about-content-secondary spacer m-top-xl">
                <div class="row gutter-width-sm">
                    <div class="col-sm-4 col-md-4 col-lg-4 col-xl-4">
                        <div class="img-no-wrap-2">
                            <div class="img object-fit">
                                <div class="object-fit-cover">
                                    <img :src="$imageUrl(mission.contImage, 'md')" alt="About Us">
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="col-sm-8 col-md-8 col-lg-8 col-xl-8 align-self-center col-last">
                        <div class="description max-width-2">
                            <template v-for="singleMission in mission.missionsList">
                              <div class="item">
                                  <h3>{{singleMission.missionTitle}}</h3>
                                  <p>{{singleMission.missionDescription}}</p>
                              </div>
                            </template>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'About-us',
        props: {
          content: {
            type: Object,
            default: {}
          },
          mission: {
            type: Object,
            default: {}
          }
        }
    }
</script>
