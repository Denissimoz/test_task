<template>
  <footer class="footer">
    <div class="container flex-r">
      <img src="@/assets/logo.png" alt="Future" class="footer-logo" />
      <div class="footer-contacts">
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
        <p class="contacts-adress">
          Адрес:
          <a href="#">
            {{ contacts.adress }}
          </a>
        </p>
        <div class="all-rights-reserved">
          © 2010 - 2014 Future. Все права защищены
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "AppFooter",
  props: {
    phone: String,
    email: String,
    adress: String
  },
  computed: {
    contacts() {
      return {
        phone: this.phone,
        email: this.email,
        adress: this.adress
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.footer {
  background-color: #fff;
  padding: 14px 0;
}

.container {
  position: relative;
  align-items: center;
}

.footer-logo {
  margin-right: 50px;
  width: 101px;
  height: 106px;
}

.footer-contacts {
  font-size: 14px;
  font-weight: bold;

  a {
    font-size: 14px;
    line-height: 1.6;
    color: #000;
  }
}

.all-rights-reserved {
  font-family: Roboto, sans-serif;
  font-size: 12px;
  font-weight: 400;
  margin-top: 12px;
  margin-bottom: -14px;
}

@media screen and (max-width: 721px) {
  .container {
    flex-direction: column;

    .footer-logo {
      margin-right: 0;
      margin-bottom: 25px;
      justify-content: center;
      align-content: center;
    }

    .footer-contacts {
      text-align: center;
    }
  }
}
</style>
