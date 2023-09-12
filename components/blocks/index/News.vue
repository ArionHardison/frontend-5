<template>
    <section id="news" class="block spacer p-top-xl">
        <div class="wrapper">
            <div class="title">
                <h2 class="hr">News</h2>
            </div>

            <div class="row gutter-width-sm with-pb-lg">
                <div v-for="newsItem in newsItems" :key="newsItem.id" class="col-xl-4 col-lg-4 col-md-4 col-sm-12">
                    <div class="card card-post">
                        <div class="card-top position-relative">
                            <router-link :title="newsItem.title" :to="newsItem.link">
                                <div class="img object-fit overflow-hidden">
                                    <div class="object-fit-cover transform-scale-h">
                                        <img class="card-top-img" :src="newsItem.imgSrc" :alt="newsItem.title">
                                    </div>
                                </div>
                            </router-link>
                        </div>

                        <div class="card-body">
                            <div class="card-meta">
                                <p>
                                    <span><router-link class="btn btn-lg btn-before-horbar btn-link border-0 p-0 min-w-auto link-no-space" :to="newsItem.categoryLink">{{ newsItem.categoryTitle }}</router-link></span>
                                </p>
                            </div>

                            <h4 class="card-title">
                                <router-link title="Which Diagnostic Should I Choose?" :to="newsItem.link">{{ newsItem.title }}</router-link>
                            </h4>

                            <p class="card-text">{{ newsItem.description }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import NewsItems from '~/data/news/newsData.json';

    export default {
        name: 'News',
        data() {
            return {
                newsItems: NewsItems.newsData
            }
        }
    }
</script>
