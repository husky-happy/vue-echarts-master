<template>
    <div class="doubleBarChart" :id="id"></div>
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
                        tooltip : {
                            trigger: 'axis',
                            axisPointer : {            // 坐标轴指示器，坐标轴触发有效
                                type : 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
                            }
                        },
                        legend: [
                            {
                                top:20,
                                right:40,
                                itemWidth:7,
                                itemHeight:7,
                                textStyle:{
                                     color:'rgb(111,223,244)',
                                },
                                data: [
                                    {name:'救援次数',icon:'rect'},
                                    {name:'找回老人次数',icon:'rect'}
                                ],
                            },
                        ],
                        grid:
                            {
                            top:'15%',
                            left: '3%',
                            right: '4%',
                            bottom:'8%',
                            containLabel: true,
                        },
                        xAxis: [
                            {
                            type: 'category',
                            axisLabel:{
                                interval:0,
                                color:'rgb(111,223,244)',
                                fontSize:10
                            },
                            axisLine:{
                            symbol:['none','arrow'],
                            symbolSize:[6,6],
                            symbolOffset:[0,10],
                             lineStyle:{
                            color:'rgb(18,44,73)'
                            }
                        },
                            axisTick:{show:false},
                             data: ['1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月']
                            },
                        ],
                        yAxis:
                            {
                            type: 'value',
                            min:0,
                            max:40,
                            axisLabel:{
                                 color:'rgb(111,223,244)',
                                fontSize:8,
                                formatter: function (value) {
                                        if(value==40){
                                        value='(次)';
                                        }
                                        return value;
                                        },
                                 showMaxLabel:true,
                            },
                            axisLine:{
                            symbol:['none','arrow'],
                            symbolSize:[6,6],
                            symbolOffset:[0,5],
                             lineStyle:{
                            color:'rgb(18,44,73)'
                            }
                        },
                            axisTick:{
                                length:3
                            },

                            splitLine:{show:false}

                        },
                        series: [

                            {
                                name: '找回次数',
                                type: 'bar',
                                 barWidth:7,
                                stack: '总数',
                                 itemStyle:{
                                     color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1,[{
                                        offset: 0, color: 'rgba(252,147,134,1)' // 0% 处的颜色
                                    },{
                                        offset: 0.4, color: 'rgba(248,123,134,1)' // 0% 处的颜色
                                    },  {
                                        offset: 1, color: 'rgba(243,96,135,1)' // 100% 处的颜色
                                    }]), //背景渐变色
                                     barBorderRadius:[3.5,3.5,0,0],
                                },
                                data: [20, 6, 15, 13, 32, 35, 25,27,12,28,12,8]
                            },
                            {
                                name: '未找回次数',
                                type: 'bar',
                                 barWidth:7,
                                stack: '总数',
                                itemStyle:{
                                    color:'#8C14EA',
                                    barBorderRadius:[3.5,3.5,0,0,],
                                },
                                data: [2, 3, 5, 3, 2, 4, 5,7,2,2,2,3]
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
    .doubleBarChart {
        width: 100%;
        height: 100%;
    }
</style>
