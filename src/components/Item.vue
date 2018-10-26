<template>
    <div :style="style" class="item" />
</template>
<script>
export default {
    name: 'Item',
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            photo: this.item.links[0].href,
            title: this.item.data[0].title,
        };
    },
    computed: {
        style() {
            return `background-image: url("${this.photo}")`;
        },
    },
};
</script>
<style lang="scss" scoped>
    .item {
        width: 100%;
        height: 250px;
        cursor: pointer;
        background-repeat: no-repeat;
        background-size: cover;
        backround-position: center;
        margin: auto;
    }
</style>