<template>
  <main class="app-content">
    <div class="container">
      <ShowComments :commentsArray="commentsArray" />
      <!-- Разделил на компоненты на слючай пагинации или подгрузки комментов -->
      <hr />
      <CreateComment @createComment="createComment" />
    </div>
  </main>
</template>

<script>
import ShowComments from "../components/comments/ShowComments.vue";
import CreateComment from "../components/comments/CreateComment.vue";
export default {
  name: "CommentPage",
  components: {
    ShowComments,
    CreateComment
  },
  data: () => ({
    commentsArray: [
      {
        id: 1,
        username: "Артемий",
        date: 1000,
        content:
          "Почему такое сложное задание??? Мне кажеться, нужно быть первоклассным программистом, что бы выполнить его :("
      },
      {
        id: 2,
        username: "Евдоким",
        date: 1000,
        content: "Если включить мозги, то всё элементарно Ватсон!"
      },
      {
        id: 3,
        username: "Савва",
        date: 1000,
        content:
          "Спасибо за Ваше тестовое задание. Оно действительно изумительное"
      },
      {
        id: 4,
        username: "Герасим",
        date: 20000,
        content: "Скучаю по Муме..."
      }
    ]
  }),
  methods: {
    createComment(comment) {
      comment = {
        id: this.commentsArray.length + 1,
        date: Date.now(),
        ...comment
      };
      this.commentsArray.push(comment);
    }
  }
};
</script>

<style scoped lang="scss">
hr {
  margin: 20px 0;
}

@media screen and (max-width: 721px) {
  .container {
    margin: 0 50px;
  }
}
</style>
