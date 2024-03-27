<template>
    <div class = "areaInfo">
			<ul class="areaTitle" style="padding: 0;" v-for="index in areaTitle[data].data" :key="index">
			    <li>
			        <div  @click="getData(index.title)">{{index.title}}</div>
			    </li>
			</ul>
    </div>
</template>
<script>
import {areaData} from '../data'
export default {
    name:'areaInfo',
    props:['titleName'],
    data(){
        return{
            data:null,
            areaTitle:areaData,
            displayInfo:null,
            show:false,
        }
    },
    created(){
        this.processData(this.titleName);
    },
    watch:{
        //进行数据更新，当titleName存在新的数据时，调用方法让响应式和newVal对应
        titleName(newVal){
            this.processData(newVal)
        }
    },
    methods: {
        processData(parentData)
        {
            this.data = parentData
        },
        getData(Element){
            if(this.displayInfo == Element){
                this.displayInfo=null
            }
            else{
                this.displayInfo = Element
            }
            // console.log(this.displayInfo)
        }
    },
}
</script>
<style>
    ul{
        list-style: none;
    }
	.areaInfo{
		display: -webkit-flex;
		display: flex;
		flex-wrap:wrap;
		width: 100%;
		height: 100%;
	}
    .areaTitle{
        width:100%;
        margin-top:1rem;
		margin-left:1.7rem;
        padding-top:10px;
        padding-left:16px;
        font-size:17.6px;
		flex:0 1 45%;
    }
    .slide-enter-active, .slide-leave-active {
        transition: all 0.5s ease;
        overflow: hidden;
    }
    .slide-enter, .slide-leave-to {
        max-height: 0;
    }
</style>