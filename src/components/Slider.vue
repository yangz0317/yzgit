<template>
<div class="slider" @mouseover="clearInv" @mouseout="runInv">
    <ul>
      <li v-for="(img, index) in imgs" :key="index" v-show="index == showIndex">
        <div class="pic">
          <img :src="'/static/'+img.src">
        </div>
        <div class="text">
            <div class="title">asd</div>
            <div class="content">1234</div>
        </div>
      </li>
    </ul>
    <div class="dots">
        <ul>
            <li class="dot" @click="showIndex = index" v-for="(img, index) in imgs" :key="index"  
        :class="index == showIndex ? 'active' : ''"></li>
        </ul>
    </div>
</div>
</template>
<script>
export default {
    data(){
        return{
            showIndex: 0, 
            timer: null,  
            show: false,
            items:[1,2,3],
            imgs:[
                {
                    src:'images/1.jpg'
                },
                {
                    src:'images/2.jpg'
                },
                {
                    src:'images/3.jpg'
                },
            ],  
        }
    },
    created () {
        this.timer = setInterval(() => {
        this.next();
        }, 3000)
    },
    beforeDestroy () {
        clearInterval(this.timer); 
    },
    methods:{
        previous(){
            if(this.showIndex <= 0){
                this.showIndex = this.imgs.length-1
            }else{
                this.showIndex --
            }
        },
        next(){
            if(this.showIndex >= this.imgs.length-1){
                this.showIndex = 0
            }else{
                this.showIndex ++
            }
        },
        clearInv(){
            clearInterval(this.timer);
        },
        runInv(){
            this.timer = setInterval(() => {
            this.next();
            }, 3000)
        }
    }
}
</script>
<style>
*{
    margin: 0;
    padding: 0;
}
.slider{
    position: relative;
    width: 100%;
    height: 500px;
    border: 1px solid #000;
}
ul li{
    /* width: 100%; */
    /* height: 100%; */
    list-style: none;
}
.pic{
    position: absolute;
    top: 10px;
    left: 10px;
}
.text{
    position: absolute;
    top: 50px;
    right: 100px;
}
.dots{
    top: 50%;
    right: 50px;
    position: absolute;
    transform: translate(0,-50%)
}
.dot{
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: #666;
    margin: 10px;
}
.active{
    background: #f00;

}
</style>

