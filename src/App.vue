<template>
    <div id="app" class="centered" :style="{'width': width + 'px'}">
            <four-child 
                v-if="isMounted"
                v-for="n in count"
                :count="count"
            ></four-child>
            
    </div>
</template>

<script>
    import fourChild from './fourChild'
    export default {
        name: 'app',
        components: {
            'four-child': fourChild
        },
        data() {
            return {
                isMounted: false,
                width: 100,
                count: 1
            }
        },
        mounted() {
            this.isMounted = true;
            setInterval(() => {
                this.width += 10;
                if (this.width % 100 === 0) {
                    this.count = this.count * 4;
                    if(this.count === 4096){
                        this.count = 1;
                    }
                    if(this.width === 1000){
                        this.width = 100;
                    }
                }
            }, 300);
    }
    }
</script>

<style>
    .centered {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        -webkit-transform: translate(-50%, -50%);
        -moz-transform: translate(-50%, -50%);
        -o-transform: translate(-50%, -50%);
        -ms-transform: translate(-50%, -50%);
        padding: 5px;
        z-index: 100;
    }
</style>