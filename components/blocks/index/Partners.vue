<template>
    <section id="partners" class="block-2 spacer p-top-xl">
        <div class="wrapper">
            <div class="title">
                <h2>Partners</h2>
            </div>

            <div class="clients">
                <div class="items">
                    <div v-for="partner in content" :key="partner.id" class="item">
                        <div class="item-content">
                            <img :src="$imageUrl(partner.plogo, 'sm')" :alt="partner.pname">
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'Partners',
        props: {
          content: {
            type: Array,
            default: []
          }
        },
    }
</script>
