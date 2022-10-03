<template>
  <a href="#header" class="btn show">
    <i class="fas fa-arrow-up"></i>
  </a>
</template>

<script>
    export default {
        name: 'Back to top'
    }
</script>

<style lang="scss">
    @import '../assets/variables.scss';

    .btn {
        display: grid;
        font-size: 1.25rem;
        position: fixed;
        bottom: 3rem;
        right: 3rem;
        background: $VeryDarkBlue;
        width: 3rem;
        height: 3rem;
        place-items: center;
        border-radius: .5rem;
        color: $White;
        visibility: hidden;
        z-index: 100;
        text-decoration: none;

        &:hover {
            cursor: pointer;
            background-color: $DarkBlue;
            transition: 1s;
        }
        
        &.show {
            opacity: 1;
            visibility: visible;
        }
    }

</style>