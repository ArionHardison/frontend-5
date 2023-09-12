<template>
    <section id="services" class="block-2">
        <div class="services">
            <div class="items clearfix">
                <router-link v-for="serviceItem in serviceItems" :key="serviceItem.id" class="item" :to="serviceItem.link">
                    <div class="item-content">
                        <h4 class="item-title">{{ serviceItem.title }}</h4>
                    </div>

                    <div class="img object-fit">
                        <div class="object-fit-cover">
                            <img :src="serviceItem.imgSrc" :alt="serviceItem.title">
                        </div>
                    </div>

                    <div class="img-bg-color"></div>
                </router-link>
            </div>
        </div>
    </section>
</template>

<script>
    import ServiceData from '~/data/services/servicesData.json';

    export default {
        name: 'ServicesList',
        data() {
            return {
                serviceItems: ServiceData.servicesData
            }
        }
    }
</script>
