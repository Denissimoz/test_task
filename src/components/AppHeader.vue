<template>
  <header class="app-header">
    <div class="container flex-r justify-between">
      <div class="header-info flex-c justify-between">
        <div class="contacts">
          <p class="contacts-phone">
            Телефон:
            <a :href="'tel:+' + contacts.phone.replace(/\D/g, '')">
              {{ contacts.phone }}
            </a>
          </p>
          <p class="contacts-email">
            Email:
            <a :href="'mailto:' + contacts.email">
              {{ contacts.email }}
            </a>
          </p>
        </div>
        <h1 class="title">
          Комментарии
        </h1>
      </div>
      <div class="header-logo">
        <img src="@/assets/logo.png" alt="Future" />
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  props: {
    phone: String,
    email: String
  },
  computed: {
    contacts() {
      return {
        phone: this.phone,
        email: this.email
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.app-header {
  width: 100%;
  background-color: #eee;
  border-bottom: 5px solid transparent;
  background-image: linear-gradient(white, white),
    linear-gradient(to bottom right, transparent 50.5%, white 50.5%),
    linear-gradient(to bottom left, transparent 50.5%, white 50.5%),
    linear-gradient(to top right, transparent 50.5%, white 50.5%),
    linear-gradient(to top left, #cccccc2a 50.5%, white 50.5%);
  background-repeat: repeat, repeat-x, repeat-x, repeat-x, repeat-x;
  background-position: 0 0, 5px 0, 5px 0, 5px 100%, 5px 100%;
  background-size: auto auto, 8px 8px, 8px 8px, 8px 8px, 8px 8px;
  background-clip: padding-box, border-box, border-box, border-box, border-box;
  background-origin: padding-box, border-box, border-box, border-box, border-box;
  box-shadow: 0 -13px 15px 8px #ccc;
  margin-bottom: 35px;
}
.title {
  font-weight: 300;
  font-size: 48px;
}

.contacts-phone {
  padding-top: 15px;
  font-size: 12pt;
  font-weight: bold;

  a {
    color: #000;
    text-decoration: none;
  }
}

.contacts-email {
  padding-top: 5px;
  font-size: 12pt;
  font-weight: bold;

  a {
    color: #000;
  }
}

.container {
  padding: 20px 0;
}

.justify-between {
  justify-content: space-between;
}

@media screen and (max-width: 721px) {
  .container {
    flex-direction: column-reverse;
    align-items: center;
  }

  .header-info {
    align-items: center;

    & h1 {
      margin-top: 40px;
    }
  }

  .contacts-phone,
  .contacts-email {
    text-align: center;
  }
}
</style>
