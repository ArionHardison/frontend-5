<template>
    <section id="partners" class="block-2 spacer p-top-xl">
        <div class="wrapper">
            <div class="title">
                <h2>Partners</h2>
            </div>

            <div class="clients">
                <div class="items">
                    <div v-for="partner in partnersItems" :key="partner.id" class="item">
                        <div class="item-content">
                            <img :src="partner.imgSrc" alt="Logo">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import PartnersData from '~/data/index/partnersData.json';

    export default {
        name: 'Partners',
        data() {
            return {
                partnersItems: PartnersData.partnersData
            }
        }
    }
</script>
