<template>
    <section id="team" class="block-2 spacer p-top-xl">
        <div class="wrapper">
            <div class="title">
                <h2>Meet Our Team</h2>
            </div>

            <div class="row gutter-width-sm with-pb-md">
                <div v-for="member in teamMembers" :key="member.id" class="col-sm-6 col-md-6 col-lg-3 col-xl-3">
                    <div class="team-member">
                        <div class="img object-fit">
                            <div class="object-fit-cover">

                                <img :src="member.imgSrc" :alt="member.position">
                            </div>
                        </div>

                        <div class="item-content">
                            <h4 class="item-t-head">{{ member.position }}</h4>

                            <div class="item-description">
                                <p><a :href="'tel:' + member.tel">{{ member.tel }}</a></p>
                                <p><a :href="'mailto:' + member.email">{{ member.email }}</a></p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import TeamData from '~/data/about/teamData.json';

    export default {
        name: 'Team',
        data() {
            return {
                teamMembers: TeamData.teamData
            }
        }
    }
</script>
