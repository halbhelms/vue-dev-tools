<template>
<img src="./info-icon.png" v-if='showIcon' class='inDev' @contextmenu.prevent="devInfo" />
<p v-show="showText" class="devInfo">{{ _name }} : {{ _description }}</p>
</template>

<script>
    export default {
        name: 'ComponentInfo',

        components: {},

        props: {
            _name: {
                type: String,
                default: 'missing'
            },
            _description: {
                type: String,
                default: 'missing'
            }
        },

        data() {
            return {
                show: false,
            }
        },

        methods: {
             devInfo() {
                this.show = !this.show
            }
        },

        computed: {
            showIcon() {
                if (this.showAllComponentInfo || this.inDev) {
                    return true
                } else {
                    return false
                }
            },
            showText() {
                if (this.showAllComponentInfo || this.show) {
                    return true
                } else {
                    return false
                }
            }
        }
    }
</script>

<style scoped>
    img.inDev {
        width: 22px;
        position: relative;
        top: 26px;
        left: 0;
        
    }
    .devInfo{
        color: gray;
        font-size: .55rem;
        display: inline-block;
        position: relative;
        top: 18px;
        font-style: italic;
        margin: 0;
        padding: 0;
    }
</style>