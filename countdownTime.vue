<template>
    <div class="countDown" :style="{'font-size':fontSize}">
        <span class="date-tiem-span h">
            <span class="tens" :style="{'background':bgColor}">{{parseInt(h/10)}}</span>
            <span class="ones" :style="{'background':bgColor}">{{(h%10)}}</span>
        </span>:
        <span class="date-tiem-span m">
            <span class="tens" :style="{'background':bgColor}">{{parseInt(m/10)}}</span>
            <span class="ones" :style="{'background':bgColor}">{{(m%10)}}</span>
        </span>:
        <span class="date-tiem-span s">
            <span class="tens" :style="{'background':bgColor}">{{parseInt(s/10)}}</span>
            <span class="ones" :style="{'background':bgColor}">{{(s%10)}}</span>
        </span>
          
    </div>
</template>
<script>
export default {
    data(){
        return{
            d:0,
            h:0,
            m:0,
            s:0,
        }
    },
    props:{
        time:{
            type:String,
        },
        fontSize:{
            type:String,
            default:'12px'
        },
        bgColor:{
            type:String,
            default:'rgba(0,0,0,.4)'
        }
    },
    methods:{
        countTime() {
            //获取当前时间
            var date = new Date();
            var now = date.getTime();
            //设置截止时间
            var endDate = new Date(this.time);
            var end = endDate.getTime();
            //时间差
            var leftTime = end - now;
            //定义变量 d,h,m,s保存倒计时的时间
            if (leftTime >= 0) {
                this.d = Math.floor(leftTime / 1000 / 60 / 60 / 24);
                this.h = Math.floor(leftTime / 1000 / 60 / 60 % 24);
                this.m = Math.floor(leftTime / 1000 / 60 % 60);
                this.s = Math.floor(leftTime / 1000 % 60);
                //递归每秒调用countTime方法，显示动态时间效果
                setTimeout(this.countTime, 1000);
            }else{
                this.d=0;
                this.h =0;
                this.m = 0;
                this.s = 0;
            }
            
        }
    },
    mounted(){
        this.countTime();
    }
}
</script>
<style lang="less" scoped>
.countDown{
    display: flex;
    justify-content: space-around;
    color: #fff;
}
.date-tiem-span{
    // padding:0 3px;
    display: flex;
    color:#fff;
    &>span{
        // background: #8c8c8c;
        background: rgba(0,0,0,.4);
        color: #fff;
        border-radius: 2px;
        // font-size: 12px;
        padding: 0px 2px;
        font-family: DIN;
        &.tens{
            margin-right: 2px;
        }
    }
}
</style>
