<template>
  <div class="hello">
    <!-- <ul>
      <li v-for="(img, index) in imgs" :key="index">
        <div class="pic">
          <img :src="'/static/'+img.src">
        </div>
      </li>
    </ul> -->
    <ul>
      <li v-for="(item,index) in items" :key="index">{{item}}</li>
    </ul>
  </div>
</template

<script>
export default {
  data(){
    return {
      showIndex: 0, 
      timer: null,  
      show: false,
      imgs:[
        {
          src:'images/1.jpg'
        },
      ],
      items:[1,2,3]   
    }
  },
}
</script>

<style scoped>
.hello{
  width: 100%;
  height: 500px;
  border: 1px solid #000;
}
</style>
