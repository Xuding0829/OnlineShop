<template>
    <el-carousel :interval="4000" height="550px" >
      <el-carousel-item v-for="item in img" :key="item.id">
        
        <img :src="item.idView" class="image">
        
      </el-carousel-item>
    </el-carousel>
</template>


<script>
import { toRefs } from 'vue';
export default {
    name: "about",
    data() {
        return {
            img : [
                {id:0, idView: require("../../assets/li.png")}, 
                {id:1, idView: require("../../assets/wang.png")},
                {id:2, idView: require("../../assets/lou.png")}
            ]
        }
    }
}
</script>
<style>
.image{
    width: 100%;
    height: inherit;
}
</style>