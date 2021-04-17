<template>
    <div class="threeBarChart" :id="id"></div>
</template>

<script>
    export default {
        name: '',
        props:{
            id:String
        },
        data() {
            return {

            }
        },
        methods: {
            setChart () {
                let option ={
                grid:{
                    top:"20%",
                    bottom:"15%",
                    left:40,
                    right:40,
                },
                tooltip : {
                    trigger: 'axis'
                },
                legend: {
                    data:[{name:'志愿者',icon:'circle'},{name:'走失老人',icon:'circle'},{name:'小程序用户',icon:'circle'}],
                    left:"8%",
                    top:"10%",
                    itemWidth:7,
                    itemHeight:7,
                    textStyle:{
                       color:'rgb(92,177,193)',
                       fontSize:10
                    }
                },
                calculable : true,
                xAxis : [
                    {
                        type : 'category',
                        axisLine:{
                            symbol:['none','arrow'],
                            symbolSize:[6,6],
                            lineStyle:{
                                color:'rgb(18,44,73)'
                            }
                        },
                        axisLabel:{
                            color:'rgb(97,185,200)',
                            showMaxLabel:false,
                            fontSize:10,
                        },
                        data : [ "2016","2017", "2018", "2019", "2021", "2022"]
                    }
                ],
                yAxis :[
                    {
                    type: 'value',
                    interval:500,
                    min:0,
                    max:4000,
                    splitNumber:7,
                    axisLine:{
                        symbol:['none','arrow'],
                        symbolSize:[6,6],
                       lineStyle:{
                           color:'rgb(18,44,73)'
                       }
                    },
                    axisLabel:{
                        color:'rgb(97,185,200)',
                        showMaxLabel:false,
                        fontSize:10,
                        formatter: function (value) {
                            if(value==3500){
                            value='(人次)';
                            }
                            return value;
                        },
                    },
                    splitLine:{
                        show:false,
                    },
                }
                ],
                series : [
                    {
                        name:'志愿者',
                        type:'bar',
                        barGap:0,
                        barWidth:6,
                        data:[2000,1800,3000,1800,2600,2300],
                        itemStyle:{
                              barBorderRadius:[3,3,0,0],
                            color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1,[{
                                        offset: 0, color: 'rgba(252,145,134,1)' // 0% 处的颜色
                                    },  {
                                        offset: 1, color: 'rgba(241,88,135,1)' // 100% 处的颜色
                                    }]), //背景渐变色
                        }
                    },
                    {
                        name:'走失老人',
                        type:'bar',
                         barGap:0,
                         barWidth:6,
                        data:[100, 209, 390, 264, 287, 380],
                        itemStyle:{
                             barBorderRadius:[3,3,0,0],
                            color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1,[{
                                        offset: 0, color: 'rgba(144,20,238,1)' // 0% 处的颜色
                                    },  {
                                        offset: 1, color: 'rgba(74,8,211,1)' // 100% 处的颜色
                                    }]), //背景渐变色
                        }
                    },
                    {
                        name:'小程序用户',
                        type:'bar',
                         barGap:0,
                         barWidth:6,
                        data:[ 3000,2700,3600,3500,3465,2800],
                        itemStyle:{
                             barBorderRadius:[3,3,0,0],
                            color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1,[{
                                        offset: 0, color: 'rgba(0,204,255,1)' // 0% 处的颜色
                                    },  {
                                        offset: 1, color: 'rgba(8,59,126,1)' // 100% 处的颜色
                                    }]), //背景渐变色
                        }
                    }
                ]
            };
             let myChart = this.$echarts.init(document.getElementById(this.id));

            myChart.clear();
            myChart.resize(
                {
                    width:document.getElementById(this.id).offsetWidth,
                height:document.getElementById(this.id).offsetHidth
                }
            )
              myChart.setOption(option);
            }
        },
        mounted() {
            this.setChart ()
        },
    }
</script>

<style lang="less" scoped>
    .threeBarChart {
        height: 100%;
        width: 100%;
    }
</style>
