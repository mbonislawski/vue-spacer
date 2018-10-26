<template>
  <div class="heroImage" />
</template>
<script>
    export default {
        name: 'HeroImage',
    };
</script>
<style lang="scss" scoped>
    .heroImage {
        position: fixed;
        top: 0;
        z-index: -1;
        height: 100vh;
        width: 100%;
        background-image: url('../assets/hero-bg.jpg');
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
    }
    .heroImage::after {
        content: '';
        width:100%;
        height: 100vh;
        background: rgba(0,0,0,0.4);
        position: absolute;
        top: 0;
        left: 0;
    }
</style>