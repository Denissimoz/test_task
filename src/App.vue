<template>
  <AppHeader :phone="contacts.phone" :email="contacts.email" />
  <CommentsPage />
  <AppFooter
    :phone="contacts.phone"
    :email="contacts.email"
    :adress="contacts.adress"
  />
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppFooter from "./components/AppFooter.vue";
import CommentsPage from "./layout/CommentsPage.vue";

export default {
  name: "App",
  components: {
    CommentsPage,
    AppHeader,
    AppFooter
  },
  data: () => ({
    contacts: {
      phone: "+7 (499) 340-94-71",
      email: "info@future-group.ru",
      adress: "115088 Москва, ул. 2-я Машиностроения, д. 7 стр. 1"
    }
  })
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

body {
  background-color: #eee;
}

#app {
  font-family: Roboto, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.container {
  margin: 0 110px;
}

.flex-c {
  display: flex;
  flex-direction: column;
}

.flex-r {
  display: flex;
  flex-direction: row;
}
</style>
