<template>
    <div class="mask">
        <div class="outerWrapper">
            <div class="innerWrapper">
                <div class="photo" :style="style" />
                <div class="description">
                    <h2 class="title">{{ title }}</h2>
                    <p class="content">
                        {{ description }}
                    </p>
                </div>
            </div>
            <div class="close" @click="$emit('closeModal')" />
        </div>
    </div>
</template>
<script>
    export default {
        name: "Modal",
        props: {
            item: {
                type: Object,
                required: true,
            },
        },
        data() {
            return {
                photo: null,
                title: null,
                description: null,
            };
        },
        mounted() {
            this.photo = this.item.links[0].href;
            this.title = this.item.data[0].title;
            this.description = this.item.data[0].description.substring(0, 200)+'...';
        },
        computed: {
            style() {
                return `background-image: url("${this.photo}")`;
            },
        },
    };
</script>
<style lang="scss" scoped>
    .mask {
        background: rgba(0,0,0,0.5);
        display: block;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
    }
    .outerWrapper {
        background: #f6f6f6;
        width: 100%;
        position: fixed;
        height: 100%;
        top: 0;
        left: 0;

        @media(min-width: 1024px) {
            max-width: 70%;
            height: 60%;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            margin: auto;
        }
    }

    .close {
        position: absolute;
        width: 30px;
        height: 30px;
        padding: 30px;
        right: 0;
        top: 0;
        cursor: pointer;

        &::before,
        &::after {
            position: absolute;
            content: '';
            top: 30px;
            right: 20px;
            width: 20px;
            height: 2px;
            background: black;
            display: block;
        }

        &::before {
            transform: rotate(45deg);
        }
        &::after {
            transform: rotate(-45deg);
        }
    }

    .innerWrapper {
        display: flex;
        height: 100%;
        padding: 30px;
        justify-content: space-between;
        align-items: center;
        flex-direction: column;

        @media(min-width: 1024px) {
            flex-direction: row;

            .photo {
                width: 50%;
                margin-right: 10px;
            }
            .description {
                width: 50%;
            }
        }

        .photo {
            width: 100%;
            height: 100%;
            margin-left: 0;
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;

            img {
                width: 100%;
            }
        }

        .description {
            color: #333;
            width: 100%;
            padding: 20px;
        }
    }
</style>