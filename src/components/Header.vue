<template>
    <header class="header">
        <nav class="header__nav">
            <h1 class="header__title">Where in the world?</h1>
            <button class="header__button" v-on:click="darkMode()"></button>
        </nav>
    </header>
</template>

<script>
    export default {
        name: 'Header',
        data() {
            return {
                darkMode() {
                    let element = document.body
                    element.classList.toggle('dark-mode')
                }
            }
        }
    }
</script>

<style lang="scss">
    @import '../assets/variables.scss';

    .header {
        padding: 2rem;
        background-color: $DarkBlue;
        box-shadow: 0px 2px 5px 0px $LightModeText;

        &__title {
            color: $White;
            font-weight: 600;
            font-size: 16px;
        }

        &__nav {
            display: flex;
            justify-content: space-around;
            align-items: center;
        }

        &__button {
            background: none;
            border: none;
            color: $White;
            cursor: pointer;
            font-size: 16px;

            &::after {
                content: ' Light Theme';
            }

            &::before {
                font-family: fontAwesome;
                content: '\f186';
            }
        }
    }

</style>