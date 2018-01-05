<template>
   <div>
        <div 
            v-for="(color, index) in colors"    
            class='square child1' 
            :key="index"
            :style="{'background-color': color, 'width': width + '%', 'padding-bottom': width + '%'}">
        </div>

    </div> 
</template>

<script>
    export default {
        props:['count'],
        data(){
            return {
                colors:["aqua", "orchid", "blue", "yellow"]
            }
        },
        computed:{
            width(){
                this.setColors();
//                this.shuffleColors();
                return 50 / Math.sqrt(this.count);
            } 
        },
        methods:{
            setColors(){
                this.colors = this.colors.map(c => this.getRandomColor())
            },
            getRandomColor(){
                return '#' + Math.floor(Math.random() * 16777215).toString(16);
            },
            shuffleColors(){
                this.colors = this.colors.map(c => {
                    let index = Math.floor(Math.random() * 4);
                    return this.colors[index];
                })
            }
        }
    }
</script>

<style>
.square {
    float: left;
    position: relative;
    background: burlywood;
}


</style>