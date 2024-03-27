<template>
    <div class="areaButton">
        <button 
        v-for="value,key in areaNameButton" :key="value" 
        @click="buttonClicked(value),sendDataToParen(key)"
        :class="['menuButton',{'clicked' : clickedButton === value}]"
        ref="value">
            {{value}}
        </button>
    </div>

</template>
<script>
import {areaData} from "../data.js"
let areaName = {}
    Object.keys(areaData).forEach(key=>{
    Object.assign(areaName,{[key]:areaData[key].name})
    })
export default {
    data(){
        return{
            //各地区的名字
            areaNameButton:areaName,
            //按钮数据
            clickedButton:'南宁'  
        };
    },
    methods: {
        //存放变量更改
        buttonClicked(key){
            this.clickedButton = key;
        },
        //子组件数据传输
        sendDataToParen(key){
            this.$emit('areaTitle',{[key]:areaName[key]});
        }
    },
}
</script>

<style>
    .menuButton{
        height:60px; 
        width: 60px;
        background-color: red;
        color: white;
        transform: 0.5s ,box-shadow 0.5s;
        margin-top:0.6rem;
        margin-left:1.5rem;
        border-radius:100%;
        border:none;
        font-size:1rem;
    }
    .clicked{
        box-shadow: 4px 4px 4px #A29D9D;
    }
</style>