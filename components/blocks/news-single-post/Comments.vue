<template>
    <div id="comments" class="comments-area spacer m-top-xl">
        <div class="comment-title">
            <h4>Comments (1)</h4>
        </div>

        <div class="position-relative">
            <ul class="comment-list list-unstyled style-default">
                <li class="comment">
                    <div class="comment-wrapper">
                        <div class="comment-details">
                            <div class="comment-header">
                                <div class="d-flex align-items-center">
                                    <div class="comment-header-right">
                                        <h5 class="comment-author">
                                            <router-link title="Rosie Ford" to="/news-single-post">Rosie Ford</router-link>
                                        </h5>
                                    </div>
                                </div>
                            </div>

                            <div class="comment-content">
                                <p>At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati.</p>
                            </div>

                            <div class="comment-reply no-space">
                                <a @click="scrollToSection('#reply-title')" title="Reply" class="comment-reply-link btn btn-lg btn-link btn-before-line p-0 border-0 min-w-auto link-no-space scroll-to-id" href="#reply-title">
                                    <i class="fas fa-reply"></i>
                                    <span>Reply</span>
                                </a>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </div>

        <div class="block spacer m-top-xl position-relative">
            <div id="respond" class="comment-respond">
                <h4 id="reply-title" class="comment-reply-title">Leave a reply <router-link rel="nofollow" id="cancel-comment-reply-link" class="btn btn-link p-0 border-0" to="/news-single-post" style="display:none;">Cancel reply</router-link></h4>

                <CommentForm />
            </div>
        </div>
    </div>
</template>

<script>
    import CommentForm from '~/components/Forms/CommentForm';

    export default {
        name: 'Comments',
        components: {
            CommentForm
        }
    }
</script>
