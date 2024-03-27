<template lang="">
    <div class="main">
        <div class="top">
        </div>
        <div class="menuButton1">
            <!-- areaTitle为menuButton传上来的参数 -->
            <menuButton @areaTitle="handleData"></menuButton>
        </div>
        <div class="pad">
			区域场景
        </div>
        <areaInfo :titleName="areaIndex" class="music"></areaInfo>
    </div>
</template>
<script>
//子组件：menuButton（生成按钮和传回目前按钮的数据）
import menuButton from "./menuButton.vue"
import areaInfo from "./areaInfo.vue"
export default {
    name:'mainPage',
    components:{
      menuButton,
      areaInfo,
    },
    data(){
      return{
        areaTitle :'南宁',
        areaIndex :'4',
      }
    },
    methods: {
      handleData(data){
        this.areaTitle = Object.values(data)[0];
        this.areaIndex = Object.keys(data)[0];
      }
    },
}

</script>
<style>
body{
  margin: 0;
  padding: 0;
  font-family: "微软雅黑";
}
.main {
  width:100%;
  height:100%;
}

.main .top{
    width: 100;
    height: 3rem;
    background-color: #f7f7f7;
    line-height: 3rem;
}
.main .top .title{
    text-align: center;
    font-size: 1.2rem;
}
.main .returnButton{
  float:left;
  margin-left:20px ;
  position: absolute;
  top: 8px;
}
.top .returnButton img{
  width: 30px;
  height: 30px;
  display: inline-block;
}
.menuButton1{
  width: 100%;
  height: 100%;
  margin-top:20px;
}
.backButton{
  height: 3rem;
  width: 100%;
  background-color: red;
  text-align: center;
  color:#fff;
  font-size: 1.3rem;
  position: fixed;
  bottom: 0;
  border: 0;
}
.pad{
  margin-top: 10px;
  width: 100%;
  margin-left:1.8rem;
  height: 2rem;
  border-bottom: 2px solid #000000;
}
.tip{
  margin:20px 16px 16px;
  font-size: 0.9rem;
  line-height: 24px;
}
.pad .areaTip{
  margin: 0 16px;
  font-size: 1.3rem;
  color:red;
}
</style>