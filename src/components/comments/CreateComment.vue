<template>
  <div class="create-comment flex-c">
    <h2 class="create-comment__title">Оставить комментарий</h2>
    <div class="input-group">
      <title for="username">Ваше имя</title>
      <input type="text" name="username" v-model="username" />
      <span v-if="errors.user" class="valid-span">{{ errors.user }}</span>
    </div>
    <div class="input-group flex-c">
      <title for="comment">Ваш комментарий</title>
      <textarea name="comment" v-model="commentContent"></textarea>
      <span v-if="errors.comment" class="valid-span">{{ errors.comment }}</span>
      <input
        type="button"
        value="Отправить"
        class="btn btn-send"
        @click="sendComment"
      />
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    username: "",
    commentContent: "",
    errors: {
      user: "",
      comment: ""
    }
  }),
  methods: {
    sendComment() {
      this.errors.comment = this.errors.user = "";
      // vuelidate не вижу смысла тут использовать
      if (!this.username) {
        this.errors.user = "Введите Ваше имя";
        return;
      } else if (this.username.length < 2) {
        this.errors.user = "Имя не менее 2 символов";
        return;
      } else if (!this.commentContent) {
        this.errors.comment = "Нельзя отправить пустой комментарий";
        return;
      } else if (this.commentContent.length < 10) {
        this.errors.comment = "Длинна комментария от 10 символов";
        return;
      } else {
        this.$emit("createComment", {
          username: this.username,
          content: this.commentContent
        });
        this.username = this.commentContent = "";
      }
    }
  }
};
</script>

<style lang="scss">
.create-comment {
  &__title {
    font-size: 32px;
    font-weight: 400;
    margin-bottom: 10px;
  }

  title {
    display: block;
    padding: 10px 0;
    font-size: 16px;
    font-weight: 400;
  }

  .input-group {
    position: relative;
    margin-bottom: 10px;
    width: 45vw;
    min-width: 350px;
    max-width: 450px;
    input {
      padding: 15px;
      width: 100%;
      height: 45px;
      border: none;
      border-radius: 3px;
      box-sizing: border-box;
      outline: none;
      font-family: Roboto, sans-serif;
      font-size: 18px;
      font-weight: 400;
      text-indent: 15px;
    }

    textarea {
      margin-bottom: 15px;
      padding: 10px 15px;
      height: 130px;
      resize: none;
      background: #eee;
      border: 2px solid #000;
      border-radius: 3px;
      box-sizing: border-box;
      outline: none;
      font-family: Roboto, sans-serif;
      font-size: 18px;
      font-weight: 400;
    }

    .btn {
      align-self: flex-end;
      width: 140px;
      padding: 15px 20px;
      border: 2px solid #000;
      border-radius: 3px;
      box-sizing: border-box;
      outline: none;
      text-indent: 0;
      font-family: Roboto, sans-serif;
      font-size: 18px;
      line-height: 10px;
      font-weight: 400;
      transition: all 0.1s ease-in;

      &:hover {
        color: #fff;
        background-color: #000;
      }

      &:active {
        transform: translateY(-1px);
      }
    }

    .valid-span {
      color: red;
    }
  }
}

@media screen and (max-width: 721px) {
  .create-comment {
    .input-group {
      max-width: 100%;
      width: 100%;
    }
  }
}
</style>
