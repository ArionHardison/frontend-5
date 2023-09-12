<template>
    <div class="row gutter-width-sm with-pb-lg" id="results">
        <div v-for="newsItem in newsItems" :key="newsItem.id" class="col-xl-6 col-lg-6 col-md-6 col-sm-6">
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
                            <span><router-link class="a-small" :to="newsItem.link">{{ newsItem.author }}</router-link></span>
                            <span class="s-small">-</span>
                            <span class="s-small">Comments ({{ newsItem.comments }})</span>
                            <span class="s-small">-</span>
                            <span class="category">
                                <router-link title="Events" class="a-small" :to="newsItem.categoryLink">{{ newsItem.category }}</router-link>
                            </span>
                        </p>
                    </div>

                    <h4 class="card-title">
                        <router-link :title="newsItem.title" :to="newsItem.link">{{ newsItem.title }}</router-link>
                    </h4>

                    <p class="card-text">{{ newsItem.description }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import NewsData from '~/data/news/newsData.json';

    export default {
        name: 'Blog',
        data() {
            return {
                newsItems: NewsData.newsData
            }
        }
    };
</script>
