<template>
  <Header />
  <Main />

  <!-- <RouterLink to="/">Home</RouterLink>
  <RouterLink to="/about">About</RouterLink> -->

  <!-- <RouterView /> -->
</template>

<script>
  // import { RouterLink, RouterView } from 'vue-router'
  import Header from './components/Header.vue'
  import Main from './components/Main.vue'

  export default {
    components: {
      Header,
      Main
    }
  }
</script>

<style lang="scss">
  @import './assets/variables.scss';

  .dark-mode {
    background: $LightGray;
    
    .header {
      background: $White;

      &__title {
        color: $LightModeText;
      }

      &__button {
        color: $LightModeText;

        &::after {
          content: ' Dark Theme';
        }

        &::before {
          content: '\f185';
        }
      }
    }

    .main {

      &__info {
        background-color: $White;
      }

      &__title {
        color: $LightModeText;
        font-weight: bold;
      }

      &__text {
        color: $LightModeText;
      }

      &__input {
        background-color: $VeryLightGray;
        color: $LightModeText;
        border: 1px solid $DarkBlue;

        &::placeholder {
          color: $LightModeText;
        }
      }

      &__button {
        background-color: $VeryLightGray;
        color: $DarkBlue;
        border: 1px solid $DarkBlue;
      }
    }
  }

  body {
    background-color: $VeryDarkBlue;
  }

  #app {
    font-family: $font;
  }

</style>