<template>
    <div class='block' v-if="showBlock" @click="stopTimer">
    click me
    </div>
</template>

<script>
import { onUnmounted } from 'vue'


export default{
        props: ['delay'],
        data(){
            return{
                showBlock: false,
                timer: null,
                reactionTime: 0
            }
        },
        mounted(){
            //console.log('mounted')    
            setTimeout(() => {
                    this.showBlock = true,this.startTimer()
                }, this.delay)
        },
        updated(){
            //console.log('updated')
        },
        unmounted(){
        //  console.log('unmounted')
        },
        methods:{
            startTimer(){
                this.timer = setInterval(() => {
                    this.reactionTime += 10
                }, 10)
            },
            stopTimer(){
                clearInterval(this.timer)
                this.showBlock = false
                this.$emit('end', this.reactionTime)            
            }
        }
    }
        /*
        updated(){
            console.log('componente actualizado')
        }
        unmounted(){
            console.log('unmounted')
        }*/
</script>
<style>
    .block{
        width: 400px;
        border-radius: 20px;
        color:red;
        text-align:center;
        background-color:blue;
    }
</style>