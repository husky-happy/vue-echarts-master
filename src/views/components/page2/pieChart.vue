<template>
    <div class="pieChart" :id="id"></div>
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
                title:[
                   {
                        text:"【志愿者】",
                        left: '12%',
                        bottom: '6%',
                        textStyle:{
                            color:"#fff",
                            fontSize:12
                        }
                   },
                   {
                        text:"【走失老人】",
                        left: '46%',
                        bottom: '6%',
                        textStyle:{
                            color:"#fff",
                            fontSize:12
                        }
                   },
                   {
                        text:"【小程序用户】",
                        right: '12%',
                        bottom: '6%',
                        textStyle:{
                            color:"#fff",
                            fontSize:12
                        }
                   }
                ],
                tooltip : {
                    trigger: 'item',
                    formatter: "{a} <br/>{b} : {c} ({d}%)"
                },
                legend: {
                    data:[
                        {name:'2016',icon:'circle'},
                        {name:'2017',icon:'circle'},
                        {name:'2018',icon:'circle'},
                        {name:'2019',icon:'circle'},
                        {name:'2020',icon:'circle'},
                        {name:'2021',icon:'circle'}
                        ],
                    left:"8%",
                    top:"10%",
                    itemWidth:7,
                    itemHeight:7,
                    textStyle:{
                       color:'#00CCFF',
                       fontSize:10
                    }
                },
                series : [
                    {
                        name: '【志愿者】',
                        type: 'pie',
                        radius : '40%',
                        center: ['17%', '60%'],
                        data:[
                            {value:2000, name:'2016'},
                            {value:1800, name:'2017'},
                            {value:3000, name:'2018'},
                            {value:1800, name:'2019'},
                            {value:2600, name:'2020'},
                          {value:2300, name:'2021'}
                        ],
                        label:{
                            fontSize:8,
                            color:'#00CCFF'
                        },
                        labelLine:{
                            length:15,
                            length2:10,
                            lineStyle:{
                                color:'#3F3F5C'
                            }
                        },
                        itemStyle: {
                            color: function (params){
                                        var colorList = ['#F74F64','#00CCFF','#315371','#142AFE','#9814FE'];
                                            return colorList[params.dataIndex];
                                        },
                            emphasis: {
                                shadowBlur: 10,
                                shadowOffsetX: 0,
                                shadowColor: 'rgba(0, 0, 0, 0.5)'
                            }
                        }
                    },
                    {
                        name: '【走失老人】',
                        type: 'pie',
                        radius : '40%',
                        center: ['50%', '60%'],
                        data:[
                          {value:100, name:'2016'},
                          {value:209, name:'2017'},
                          {value:390, name:'2018'},
                          {value:264, name:'2019'},
                          {value:287, name:'2020'},
                          {value:380, name:'2021'}
                        ],
                        label:{
                            fontSize:8,
                            color:'#00CCFF'
                        },
                        labelLine:{
                            length:15,
                            length2:10,
                            lineStyle:{
                                color:'#3F3F5C'
                            }
                        },
                        itemStyle: {
                            color: function (params){
                                        var colorList = ['#F74F64','#00CCFF','#315371','#142AFE','#9814FE'];
                                            return colorList[params.dataIndex];
                                        },
                            emphasis: {
                                shadowBlur: 10,
                                shadowOffsetX: 0,
                                shadowColor: 'rgba(0, 0, 0, 0.5)'
                            }
                        }
                    },
                    {
                        name: '【小程序用户】',
                        type: 'pie',
                        radius : '40%',
                        center: ['82%', '60%'],
                        data:[
                          {value:3000, name:'2016'},
                          {value:2700, name:'2017'},
                          {value:3600, name:'2018'},
                          {value:3500, name:'2019'},
                          {value:3465, name:'2020'},
                          {value:2800, name:'2021'}
                        ],
                        label:{
                            fontSize:8,
                            color:'#00CCFF'
                        },
                        labelLine:{
                            length:15,
                            length2:10,
                            lineStyle:{
                                color:'#3F3F5C'
                            }
                        },
                        itemStyle: {
                            color: function (params){
                                        var colorList = ['#F74F64','#00CCFF','#315371','#142AFE','#9814FE'];
                                            return colorList[params.dataIndex];
                                        },
                            emphasis: {
                                shadowBlur: 10,
                                shadowOffsetX: 0,
                                shadowColor: 'rgba(0, 0, 0, 0.5)'
                            }
                        }
                    },
                ]
            };
            let myChart = this.$echarts.init(document.getElementById(this.id));

            myChart.clear();
            myChart.resize(
                {
                    width:document.getElementById(this.id).width,
                height:document.getElementById(this.id).heidth
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
    .pieChart {
        height: 100%;
        width: 100%;
        padding:0 20px;
    }
</style>
