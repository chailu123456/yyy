<template>
    <div class="decolist">
       <div class="allimg">
            <span v-for="imgA in allimg">
                <img v-lazy="'https://www.yishechina.cn/attachs/'+imgA.photo" alt="">
            </span>
       </div>
    </div>
</template>

<script>
import axios from 'axios'
import { Lazyload} from 'vant';
export default {
    name:'decorList',
    data(){
        return{
            txtIdone :4,
            txtIdtwo  :5,
            allimg:[]
        }
    },
    created(){
        this.decote()
    },
    methods:{
        decote(){
            axios({
                url:"https://www.yishechina.cn/wapp/index.php/Home/Index/sort_case/id/"+this.txtIdone+','+this.txtIdtwo}).then(res=>{
                console.log(res)
                this.allimg = res.data;
            })
        },
    }
}
</script>

<style scoped>
.decolist {
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    background: white;
    overflow-x: hidden;
    text-align:left;
}
.allimg {
    width: 100%;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
.allimg span {
    width: 44%;
    margin-top: 6px;
}
.allimg span img {
    width: 100%;
    height: 120px;
    
}
</style>
