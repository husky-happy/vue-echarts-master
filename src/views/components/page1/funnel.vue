<template>
    <div class="funnel" :id="id"></div>
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
            // 手机安全分析
            setChart () {
                let option = {
                    tooltip: {
                        trigger: 'item',
                        formatter: "{b} : {c}",
                         backgroundColor:'#11367a',
                            textStyle:{
                                color:'#6dd0e3',
                                fontSize:10,
                            },
                    },

                    legend:{
                        top: '17%',
                        right: "7%",
                        orient:"vertical",
                        itemWidth:0,
                        itemGap:55,
                        textStyle:{
                            color:'#75deef',
                            fontSize:14
                        },
                        data:['累计救援时长','累计出队人数','在册志愿者','累计任务数量','累计找回老人数量']
                    },
                    series: [
                        {
                            name: '预期',
                            type: 'funnel',
                            left: 20,
                            width: '60%',
                                height:'75%',
                            label: {

                                normal: {
                                    show:false,
                                    formatter: '{b}预期',
                                    position:'right'
                                },
                                emphasis: {
                                    show:false,
                                    position:'inside',
                                    formatter: '{b}预期: {c}%'
                                }
                            },
                            labelLine: {
                                normal: {
                                    show: false
                                }
                            },
                            itemStyle: {
                                normal:{
                                    borderWidth:0,
                                        opacity: .7,
                                    color: function (params){

                                    var colorList = [
                                            '#2c7afc','#bd2229','#a262f2','#fe672c','#27fcfe'
                                            ];
                                        return colorList[params.dataIndex];
                                    }
                                },

                            },
                            data: [
                              {value: 100000, name: '累计救援时长'},
                              {value: 80000, name: '累计出队人数'},
                              {value: 60000, name: '在册志愿者'},
                              {value: 40000, name: '累计任务数量'},
                              {value: 35000, name: '累计找回老人数量'}
                            ]
                        },
                        {
                            name: '实际',
                            type: 'funnel',
                            left: 20,
                            height:'75%',
                            width: '60%',
                            maxSize: '60%',
                            z:3,
                            label: {
                                normal: {
                                    position: 'inside',
                                    formatter: '{c}',
                                    textStyle: {
                                        color: '#fff'
                                    }
                                },
                                emphasis: {
                                    position:'inside',
                                }
                            },
                            itemStyle: {
                                normal:{
                                        opacity: .5,
                                        borderWidth:0,
                                    color: function (params){
                                    var colorList = [
                                            'rgb(44,123,254)','rgb(194,35,42)','rgb(162,98,242)','rgb(254,103,44)','rgb(44,252,254)'
                                            ];
                                        return colorList[params.dataIndex];
                                    }
                                },
                            },
                            data: [
                              {value: 100000, name: '累计救援时长'},
                              {value: 80000, name: '累计出队人数'},
                              {value: 60000, name: '在册志愿者'},
                              {value: 40000, name: '累计任务数量'},
                              {value: 35000, name: '累计找回老人数量'}
                            ]
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
            },
        },
        mounted() {
            this.setChart ()
        },
    }
</script>

<style lang="less" scoped>
    .funnel {
        width: 100%;
        height: 100%;
    }
</style>
