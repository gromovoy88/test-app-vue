<template>
  <div class="post-item">
    <div class="post-item-title">
      <span>Post id.{{ post.id }}. {{post.title}}</span>
    </div>
    <div class="post-item-body">
      <p>{{post.body}}</p>
    </div>
    <div class="post-item-comments">
      <comment-list :comments="postsComments"/>
      <a
        class="activator"
        :class="isShowComments ? 'show-comments' : 'hide-comments'"
        @click="isShowComments = !isShowComments"
      >
        <span>{{ isShowComments ? 'Show comments' : 'Hide comments' }}</span>
      </a>
    </div>
  </div>
</template>

<script>
import { store } from '@/store';
import MCommentList from '@/components/molecules/M-CommentList.vue';

export default {
  name: 'PostItem',
  props: {
    post: Object,
  },
  components: {
    'comment-list': MCommentList,
  },
  data() {
    return {
      postId: this.post.id,
      isShowComments: false,
    };
  },
  computed: {
    postsComments() {
      return store.comments.filter((post) => post.post_id === this.post.id);
    },
  },
};
</script>

<style scoped lang="scss">
</style>
