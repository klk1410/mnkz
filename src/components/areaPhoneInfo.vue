<template lang="">
    <el-collapse-transition>
        <div class="areaPhoneInfo">
            <ul v-for="index in handleInfo" :key="index"
            class="info">
                <li class="areaName listPublic">{{Object.keys(index)[0]}}</li>
                <li class="phoneNumber listPublic">{{Object.values(index)[0]}}</li>
                <li >
                    <a href="">
                        <button class="callNumber listPublic">拨打</button>
                    </a>
                </li>
            </ul>
        </div>
    </el-collapse-transition>
</template>
<script>
//1.根据父组件传回来的handleData，读取传回来的数据的电话信息（已完成）
//2.根据父组件传回来的信息，决定对应的areaPhoneInfo区域的display是否为block
import { ElCollapseTransition } from 'element-plus'
export default {
    name:'areaPhoneInfo',
    props:['handleData'],
    components:{
        ElCollapseTransition
    },
    data(){
        return{
            //数据初始化
            handleInfo:null,
        }
    },
    created(){
        //挂载时初始值设定为传递数据
        this.processData(this.handleData)
        // console.log(this.processData(this.handleData))
        // debugger;
    },
    watch:{
        //监控handleInfo的数据变化，用processData方法更新数据
        handleData(newVal){
            this.processData(newVal)
            // console.log(this.processData)
        },
    },
    methods: {
        //更新handleData数据
        processData(parentData){
            // console.log(this.handleInfo)
            this.handleInfo = parentData
            // console.log(parentData)
            // console.log(this.handleInfo)
        },
    },
}
</script>
<style>
    .info{
        margin: 0;
        height: 40px;
        line-height: 40px;
        font-size: 0.8rem;
    }
    .listPublic{
        float:left;

    }
    .areaName{
        width:38%;
        margin-left:-26px;
    }
    .phoneNumber{
        width:44%;
    }
    .areaPhoneInfo{
        border:1px solid #e8e8e8;
        display: grid;
        margin: 0px 16px;
        border-radius: 10px;
    }
    .callNumber{
        border: 1px solid red;
        margin-top:8px;
        background-color: #fff;
        width:54px;
        height: 24px;
        border-radius:10px
    }
</style>