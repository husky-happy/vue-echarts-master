<template>
    <div class="doubleLine" :id="id"></div>
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
                let option = {
                tooltip: {
                    trigger: 'axis'
                },
                legend: {
                    data:[{
                        name:'找回次数',
                        icon:'circle'
                    },
                    {
                        name:'未找回次数',
                        icon:'circle'
                    }
                        ],
                    left:"11%",
                    top:"12%",
                    itemWidth:7,
                    itemHeight:7,
                    textStyle:{
                       color:'rgb(92,177,193)',
                       fontSize:10,
                    }
                },
                grid: {
                    top:40,
                    left: 10,
                    right: 10,
                    bottom: 10,
                    containLabel: true
                },

                xAxis: {
                        type: 'category',
                        boundaryGap: false,
                        axisLine:{
                            symbol:['none','arrow'],
                            symbolSize:[6,6],
                            symbolOffset:[0,10],
                             lineStyle:{
                            color:'rgb(18,44,73)'
                            }
                        },
                        axisTick:{show:false},
                        axisLabel:{
                            inside:true,
                             color:'rgb(97,185,200)',
                             fontSize:10
                        },
                        data: ["2016", "2017", "2018", "2019", "2021", "2022"]
                    },
                yAxis: [
                     {
                        type: 'value',
                        scale: true,
                        max: 400,
                        min: 0,
                        interval:50,
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
                                if(value==350){
                                value='(次)';
                                }
                                return value;
                            },
                        },
                        splitLine:{
                            show:false,
                        },
                    },
                    {
                        type: 'value',
                        scale: true,
                        max: 400,
                        min: 0,
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
                                if(value==350){
                                value='(次)';
                                }
                                return value;
                            },
                        },
                        interval:50,
                        splitLine:{
                            show:false,
                        },
                    }
                ],
                series: [
                    {
                        name:'找回次数',
                        type:'line',
                        smooth:true,
                        symbol: 'none',
                        lineStyle:{
                            color:'#F39800',
                        },
                        itemStyle:{
                            color:'#F39800'
                        },
                        data:[200, 132, 100, 300, 190, 230]
                    },
                    {
                        name:'未找回次数',
                        yAxisIndex:1,
                        type:'line',
                        smooth:true,
                        symbol: 'none',
                        lineStyle:{
                            color:'#BF232A',

                        },
                        itemStyle:{
                            color:'#BF232A'
                        },
                        data:[60, 100,60, 80, 90, 70]
                    },
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
    .doubleLine {
        height: 100%;
        width: 100%;
    }
</style>
