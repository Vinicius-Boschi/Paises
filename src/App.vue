<template>
  <Header />
  <Main />
  <BackToTop />
</template>

<script>
  import Header from './components/Header.vue'
  import Main from './components/Main.vue'
  import BackToTop from './components/BackToTop.vue'

  export default {
    components: {
      Header,
      Main,
      BackToTop
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

    .btn {
      background-color: $LightModeInput;

      &:hover {
        background-color: $LightGray;
        color: $DarkBlue;
      }
    }
  }

  * {
    scroll-behavior: smooth;
  }

  body {
    background-color: $VeryDarkBlue;
  }

  #app {
    font-family: $font;
    
  }

</style>