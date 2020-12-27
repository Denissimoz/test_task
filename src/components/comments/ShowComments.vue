<template>
  <ul class="comments-list">
    <li v-for="comment in comments" :key="comment.id" class="comment-item">
      <div class="comment-item__title">
        <div class="comment-item__username">{{ comment.username }}</div>
        <div class="comment-item__date">
          <span class="time">
            {{ new Date(comment.date).toLocaleString().slice(12, 17) }}
          </span>
          <span class="date">
            {{ new Date(comment.date).toLocaleString().slice(0, 10) }}
          </span>
        </div>
      </div>
      <p class="comment-item__content">{{ comment.content }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    commentsArray: Array
  },
  computed: {
    comments() {
      return this.commentsArray;
    }
  }
};
</script>

<style lang="scss">
.comments-list {
  display: flex;
  flex-direction: column-reverse;
  list-style: none;
}

.comment-item {
  padding: 20px 0;

  &__title {
    width: 280px;
    display: flex;
    justify-content: space-between;
    padding-bottom: 16px;
  }

  &__username {
    font-size: 20px;
    font-weight: 600;
  }

  &__date {
    font-size: 12px;
    font-weight: 400;
    align-self: center;

    .time {
      margin-right: 10px;
    }
  }

  &__content {
    font-size: 16px;
  }
}
</style>
