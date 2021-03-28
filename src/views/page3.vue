<template>
    <div class="mapList">
        <Row class="charts">
            <Col style="width:26%;">
                <div class="left">
<!--                    <span class='title'><span class="title-text">网赌网炒风险分析</span></span>-->
                    <span class="angle1"></span>
                    <span class="angle2"></span>
                    <span class="angle3"></span>
                    <span class="angle4"></span>
                    <div class="left1" style="height:50%;">
                        <div style="height:50%;">
                        <avatar src="https://z3.ax1x.com/2021/03/28/cpQM5T.png" style="width: 300px;height: 150px" class="logo"></avatar>
                        </div>
                        <div style="height: 50%;display: flex">
                            <div style="height: 100%; width: 50%;">
                                 <pie ref="chart3" id="pie_1" :data="pieData1"></pie>
                            </div>
                            <div style="height: 100%; width: 50%;">
                                 <pie ref="chart3" id="pie_3" :data="pieData2"></pie>
                            </div>
                        </div>
                    </div>
                    <div class="left1" style="height:50%;">
<!--                        <red-pocket ref="redPocket"></red-pocket>-->
                      <funnel ref="chart16" id="bottom_8"></funnel>
                    </div>
                </div>
            </Col>
            <Col style="width:48%;padding:0 1%;">
                <div class="center-top">
                    <china-map ref="chinaMap"></china-map>
                </div>
                <div class="center-bottom">
                    <span class='title'><span class="title-text">年度救援任务统计</span></span>
                    <span class="angle1"></span>
                    <span class="angle2"></span>
                    <span class="angle3"></span>
                    <span class="angle4"></span>
                  <div class="chart-68" >
                    <area-chart ref="chart1" id="left_7" :data="chatLineData"></area-chart>
                  </div>
                  <div class="chart-32">
                    <radar-chart ref="chart2" id="left_8" :data="chatRadarData"></radar-chart>
                  </div>
                </div>
            </Col>
            <Col style="width:26%">
                <div class="right-1">
                    <div class="right1-1">
                        <span class='title'><span class="title-text">志愿者排行</span></span>
                        <span class="angle1"></span>
                        <span class="angle2"></span>
                        <span class="angle3"></span>
                        <span class="angle4"></span>
                        <webcasts-risk ref='webcastsRisk'></webcasts-risk>
                    </div>
                </div>
                <div class="right-1">
                    <div class="right1-1">
                        <span class='title'><span class="title-text">地区排行</span></span>
                        <span class="angle1"></span>
                        <span class="angle2"></span>
                        <span class="angle3"></span>
                        <span class="angle4"></span>
                        <device-safe-risk ref='deviceSafeRisk'></device-safe-risk>
                    </div>
                </div>
                <div class="right-2">
                    <div class="right1-1">
                        <span class='title'><span class="title-text">救援任务完成统计</span></span>
                        <span class="angle1"></span>
                        <span class="angle2"></span>
                        <span class="angle3"></span>
                        <span class="angle4"></span>
                      <div class="circlePie">
                        <canvas id="main" width="500" height="500"></canvas>
                        <canvas id="dot" width="500" height="500"></canvas>
                      </div>
                    </div>
                </div>
            </Col>
        </Row>
    </div>
</template>

<script>
    import chinaMap from './components/page3/chinaMap.vue';
    import channelBar from './components/page3/channelBar.vue';
    import distributionSolider from './components/page3/distributionSolider.vue';
    import pie from './components/pie.vue';
    import redPocket from './components/page3/redPocket.vue';
    import radar from './components/radar.vue';
    import doubleBar from './components/page3/doubleBar.vue';
    import webcastsRisk from './components/page3/webcastsRisk.vue';
    import deviceSafeRisk from './components/page3/deviceSafeRisk.vue';
    import doubleRing from './components/page3/doubleRing.vue';
    import hotWords from './components/page3/hotWords.vue';
    import $ from "jquery";
    import areaChart from './components/page2/areaChart.vue'
    import radarChart from './components/radar.vue'
    import funnel from './components/page1/funnel.vue';

    export default {
        name: '',
        components: {
          areaChart,
          radarChart,
            chinaMap,
            channelBar,
            distributionSolider,
            pie,
            redPocket,
            radar,
            doubleBar,
            webcastsRisk,
            deviceSafeRisk,
            doubleRing,
            hotWords,
            funnel
        },
        data() {
            return {
              everyPer:0,
              xOffset:0,
              IsdrawCircled:false,
              circle: {
                x: 250,
                y: 250,
                radius: 218
              },
              title:['累计任务数量:456,789','累计出队人数:123,12','累计救援时长:134,23','累计找回老人数量:234,234','在册志愿者数量:123,123','注册用户数量:678,123'],
              warea: {x: 250, y: 250, max: 700},
                dots: [],
              chatLineData:[
                {
                  name:'救援次数',
                  color:['158,112,255','110,94,255'],
                  data: [23, 8, 15, 16, 32, 43, 25,31,12,32,22,8],
                },
                {
                  name:'找回老人次数',
                  color:['72,206,253','83,86,241'],
                  data: [20, 6, 15, 13, 32, 43, 25,27,12,28,12,8],
                }
              ],
              chatRadarData: {
                title:'救援队能力评估',
                position:['center', '85%'],
                center: ['50%', '50%'],
                indicator: [
                  { text: '救援速度',max:100 },
                  { text: '凝聚力',max:100  },
                  { text: '任务完成率' ,max:100 },
                  { text: '出队速度',max:100  },
                  { text: '善后工作',max:100  },

                ],
                data: [
                  {
                    name: '能力评估',
                    color: '#0DF5F8',
                    value: [85, 80, 75, 85, 90],
                  }
                ]
              },
                data1: [
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '20%',
                        data: {name: "红包转账", value: 45, color: '#0E4CFF'},
                    },
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '36%',
                        data: {name: "访问涉赌网络", value: 60, color: '#B405FD'},
                    },
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '53%',
                        data: {name: "使用涉赌应用", value: 12, color: '#FE9900'},
                    },
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '69%',
                        data: {name: "访问炒股网络", value: 24, color: '#FF6600'},
                    },
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '85%',
                        data: {name: "使用炒股应用", value: 21, color: '#7F05FD'}

                    }
                ],
                data3: [
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '29%',
                        data: {name: "红包转账", value: 45, color: '#0E4CFF'},
                    },
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '54%',
                        data: {name: "访问涉赌应用", value: 60, color: '#FE9900'},
                    },
                    {
                        subtitle: '675人（2345次/4533元）',
                        top: '78%',
                        data: {name: "使用炒股应用", value: 12, color: '#7F05FD'},
                    },
                ],
                data2: [ // 网赌用户排名数据
                    {
                        top: '16%',
                        color: '14,73,245',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                    {
                        top: '34%',
                        color: '170,6,243',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                    {
                        top: '50%',
                        color: '254,153,0',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                    {
                        top: '68%',
                        color: '255,102,0',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                    {
                        top: '85%',
                        color: '127,5,253',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                ],
                data4: [
                    {
                        top: '30%',
                        color: '14,73,245',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                    {
                        top: '57%',
                        color: '254,153,0',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                    {
                        top: '83%',
                        color: '127,5,253',
                        data: [
                            {name: '王立国', value: 10},
                            {name: '李建国', value: 9},
                            {name: '董年月', value: 8},
                            {name: '高树安', value: 7},
                            {name: '李白', value: 6},
                            {name: '杜甫', value: 5},
                            {name: '刘禹锡', value: 4},
                            {name: '苏东坡', value: 3},
                            {name: '杜牧', value: 2},
                            {name: '李白', value: 1},
                        ],
                    },
                ],
                data5: {
                    title: '社会应用分析',
                    position: ['5%', '14%'],
                    center: ['50%', '60%'],
                    indicator: [
                        {text: '微信'},
                        {text: 'QQ'},
                        {text: '微博'},
                        {text: '陌陌'},
                        {text: 'INS'},
                        {text: '抖音'}
                    ],
                    data: [
                        {
                            name: '安装量',
                            color: '#0DE4EE',
                            value: [100, 8, 0.40, -80, 2000, 345]
                        },
                        {
                            name: '使用时长',
                            color: '#0D88F3',
                            value: [60, 5, 0.30, -100, 1500, 232]
                        }
                    ]
                },
                data6: {
                    title: '涉军信息分析',
                    position: ['5%', '14%'],
                    center: ['50%', '60%'],
                    indicator: [
                        {text: '微信'},
                        {text: 'QQ'},
                        {text: 'SNS'},
                        {text: '漂流瓶'},
                        {text: '陌陌'},
                        {text: '摇一摇'},
                        {text: 'INS'},
                        {text: '抖音'},
                    ],
                    data: [
                        {
                            name: '个人信息涉军',
                            color: '#6514FF',
                            value: [100, 8, 0.40, -80, 2000, 345, 12, 654]
                        },
                        {
                            name: '内容涉军',
                            color: '#B370FD',
                            value: [60, 5, 0.30, -100, 1500, 232, 432, 43]
                        }
                    ]
                },
                data7: {
                    title: '交友方式分析',
                    position: ['5%', '14%'],
                    center: ['50%', '60%'],
                    indicator: [
                        {text: '面对面'},
                        {text: '手机号'},
                        {text: '手机联系人'},
                        {text: '摇一摇'},
                        {text: '微博'},
                        {text: '微信'},
                        {text: '名片'},
                        {text: '快手'},
                        {text: 'INS'},
                        {text: '扫一扫'},
                        {text: '附近的人'},
                        {text: '漂流瓶'},
                    ],
                    data: [
                        {
                            name: '主动',
                            color: '#0096FE',
                            value: [100, 8, 0.40, -80, 2000, 345, 123, 21, 34, 54, 431, 876]
                        },
                        {
                            name: '被动',
                            color: '#9EEAFF',
                            value: [60, 5, 0.30, -100, 1500, 232, 78, 32, 567, 43, 765, 432,]
                        }
                    ]
                },
                data8: {
                    title: '群属性分析',
                    position: ['5%', '14%'],
                    center: ['50%', '60%'],
                    indicator: [
                        {text: '博彩群'},
                        {text: '涉赌群'},
                        {text: '营销群'},
                        {text: '其他'},
                        {text: '相亲群'},
                        {text: '涉黄群'},
                    ],
                    data: [
                        {
                            name: '微信',
                            color: '#FD9800',
                            value: [100, 8, 0.40, -80, 2000, 345],
                        },
                        {
                            name: 'QQ',
                            color: '#FDC673',
                            value: [60, 5, 0.30, -100, 1500, 232]
                        }
                    ]
                },
                data9: {
                    title: '重点关注用户',
                    data: [
                        {
                            name: '个数',
                            color: '#00CCFF',
                            value: ['112', '212', '42', '232', '123', '67'],
                        },
                        {
                            name: '使用时长',
                            color: '#142AFE',
                            value: ['112', '212', '42', '232', '123', '67']
                        }
                    ]
                },
                data10: {
                    title: '重点关注用户',
                    data: [
                        {
                            name: '个人信息涉军应用个数',
                            color: '#6514FF',
                            value: ['112', '212', '42', '232', '123', '67'],
                        },
                        {
                            name: '涉军内容条数',
                            color: '#B370FD',
                            value: ['112', '212', '42', '232', '123', '67']
                        }
                    ]
                },
                data11: {
                    title: '重点关注异常交友用户',
                    data: [
                        {
                            name: '主动',
                            color: '#05467D',
                            value: ['112', '212', '42', '232', '123', '67'],
                        },
                        {
                            name: '被动',
                            color: '#52B8FF',
                            value: ['112', '212', '42', '232', '123', '67']
                        }
                    ]
                },
                data12: {
                    title: '重点关注用户',
                    data: [
                        {
                            name: '个数',
                            color: '#FD9800',
                            value: ['112', '212', '42', '232', '123', '67'],
                        },
                        {
                            name: '使用时长',
                            color: '#FDC673',
                            value: ['112', '212', '42', '232', '123', '67']
                        }
                    ]
                },
                pieData1:{// 饼图数据1
                    title:"年龄占比",
                    color:'#2C7BFE',

                    data:[
                        {
                            value:40,
                            name:'60-69岁',
                            itemStyle:{
                                color:'#1456FE'
                            }

                        },
                        {
                            value:60,
                            name:'70-79岁',
                            itemStyle:{
                                color:'#00CCFF'
                            }
                        },
                        {
                            value:80,
                            name:'80-89岁',
                            itemStyle:{
                                color:'#142AFE'
                            }
                        }
                    ],
                },
                pieData2:{// 饼图数据1
                    title:"任务时长占比",
                    color:'#2C7BFE',

                    data:[
                        {
                            value:60,
                            name:'2小时以内',
                            itemStyle:{
                                color:'#142AFE'
                            }

                        },
                        {
                            value:20,
                            name:'2-4小时',
                            itemStyle:{
                                color:'#1493FE'
                            }
                        },
                        {
                            value:80,
                            name:'4-6小时',
                            itemStyle:{
                                color:'#252448'
                            }
                        },
                        {
                            value:40,
                            name:'6-8小时',
                            itemStyle:{
                                color:'#00CCFF'
                            }
                        },
                        {
                            value:40,
                            name:'8小时以上',
                            itemStyle:{
                                color:'#1456FE'
                            }
                        }
                    ],
                },
                pieData3:{// 饼图数据1
                    title:"TOP数据3",
                    color:'#2C7BFE',

                    data:[
                        {
                            value:60,
                            name:'分类1',
                            itemStyle:{
                                color:'#1493FE'
                            }

                        },
                        {
                            value:20,
                            name:'分类2',
                            itemStyle:{
                                color:'#142AFE'
                            }
                        },
                        {
                            value:80,
                            name:'分类3',
                            itemStyle:{
                                color:'#1456FE'
                            }
                        },
                        {
                            value:40,
                            name:'分类4',
                            itemStyle:{
                                color:'#00CCFF'
                            }
                        },
                        {
                            value:40,
                            name:'分类5',
                            itemStyle:{
                                color:'#252448'
                            }
                        }
                    ],
                },
            }
        },
      methods: {
        drawDot () {
          let canvas = document.getElementById('dot');
          let ctx = canvas.getContext('2d');
          ctx.clearRect(0, 0, canvas.width, canvas.height);
          let that = this;


          // 将鼠标坐标添加进去，产生一个用于比对距离的点数组

          var ndots = [that.warea].concat(that.dots);

          that.dots.forEach(function(dot) {




            // 粒子位移

            dot.x += dot.xa;

            dot.y += dot.ya;




            // 遇到边界将加速度反向

            dot.xa *= (dot.x > canvas.width || dot.x < 0) ? -1 : 1;

            dot.ya *= (dot.y > canvas.height || dot.y < 0) ? -1 : 1;




            // 绘制点
            ctx.fillStyle = '#ffffff';
            ctx.beginPath();
            ctx.arc(dot.x - 0.5,dot.y - 0.5, 1, 0, 2*Math.PI, true);
            ctx.closePath();
            ctx.fill();




            // 循环比对粒子间的距离

            for (var i = 0; i < ndots.length; i++) {

              var d2 = ndots[i];
              if (dot === d2 || d2.x === null || d2.y === null) continue;
              var xc = dot.x - d2.x;

              var yc = dot.y - d2.y;




              // 两个粒子之间的距离

              var dis = xc * xc + yc * yc;




              // 距离比

              var ratio;




              // 如果两个粒子之间的距离小于粒子对象的max值，则在两个粒子间画线

              if (dis < d2.max) {




                // 如果是鼠标，则让粒子向鼠标的位置移动

                if (d2 === that.warea && dis > (d2.max / 2)) {

                  dot.x -= xc * 0.03;

                  dot.y -= yc * 0.03;

                }




                // 计算距离比

                ratio = (d2.max - dis) / d2.max;




                // 画线

                ctx.beginPath();

                ctx.lineWidth = ratio / 2;
                if (d2 == that.warea) {
                  ctx.strokeStyle = 'rgba(0,0,0,0)';
                } else {
                  ctx.strokeStyle = 'rgba(0,0,0,' + (ratio + 0.2) + ')';
                }



                ctx.moveTo(dot.x, dot.y);

                ctx.lineTo(d2.x, d2.y);

                ctx.stroke();

              }

            }




            // 将已经计算过的粒子从数组中删除

            ndots.splice(ndots.indexOf(dot), 1);

          });
          window.requestAnimationFrame(this.drawDot);
        },
        rads(x) { // 弧度转换
          return Math.PI * x / 180;
        },
        act(){
          //清空画布
          let context = $("#main").get(0).getContext('2d');
          context.clearRect(0,0,$("#main").get(0).width,$("#main").get(0).height);
          this.drawPie(this.everyPer);
          window.requestAnimationFrame(this.act);
          this.everyPer += Math.PI/180;
          var speed = 0.07; //波浪速度，数越大速度越快
          this.xOffset += speed;

        },
        drawPie (everyPer) {
          let context = $("#main").get(0).getContext('2d');
          context.save();
          context.fillStyle = 'rgba(18,55,88,.2)';
          context.beginPath();
          context.arc(this.circle.x,this.circle.y, 245, 0, 2*Math.PI, true);
          context.closePath();
          context.fill();
          context.restore();

          //外圆
          context.save();
          context.shadowBlur=50;
          context.shadowColor="#123959";
          context.fillStyle = '#080D27';
          context.beginPath();
          context.arc(this.circle.x,this.circle.y, 235, 0, 2*Math.PI, true);
          context.closePath();
          context.fill();
          context.restore();
          for (let i = 0; i < 6; i++){//绘制文字。
            context.save()
            this.drawCircularText(this.circle,this.title[i], this.rads(i*60-110), this.rads(i*60-65),i);
            context.restore();
          }
          // 旋转小球
          var x = 240 * Math.cos(everyPer);
          var y = 240 * Math.sin(everyPer);
          context.save();
          context.fillStyle='rgb(56,252,253)';
          context.shadowBlur=80;
          context.shadowColor="#39E9EE";
          context.translate(this.circle.x,this.circle.y);
          context.beginPath();
          // context.arc(x,y,5,0,2*Math.PI);
          // context.arc(-x,-y,5,0,2*Math.PI);
          context.closePath();
          context.fill();
          context.restore();
          //
          context.save();
          context.fillStyle = '#153776';
          context.beginPath();
          context.arc(this.circle.x,this.circle.y, 200, 0, 2*Math.PI, true);
          context.closePath();
          context.fill();

          context.fillStyle = "#121535";
          context.beginPath();
          context.arc(this.circle.x,this.circle.y, 190, 0, 2*Math.PI, true);
          context.closePath();
          context.fill();
          //内圆
          var nowRange = 80;
          context.save();
          if (this.IsdrawCircled == false) {
            this.drawCircle (context);
          }

          this.drawSin(this.xOffset,context,nowRange);
          this.drawText(context,nowRange);
          context.restore();
          for (let i = 0; i < 6; i++){//绘制刻度。
            context.save();
            context.translate(this.circle.x,this.circle.y);
            context.rotate((-Math.PI/2+Math.PI/6)+ i * Math.PI/3);  //旋转坐标轴。坐标轴x的正方形从 向上开始算起
            context.beginPath();
            context.moveTo(190, 0);
            context.lineTo(200, 0);
            context.lineWidth =4;
            context.strokeStyle ='#0A122D';
            context.stroke();
            context.closePath();
            context.restore();
          }
        },
        drawCircle (ctx){ // 画圆
          ctx.beginPath();
          ctx.fillStyle = '#209ADF';
          ctx.arc(this.circle.x,this.circle.y, 120, 0, 2 * Math.PI);
          ctx.fill();
          ctx.beginPath();
          ctx.arc(this.circle.x,this.circle.y, 120, 0, 2 * Math.PI);
          ctx.clip();

        },
        drawSin (xOffset,ctx,nowRange){ //画sin 曲线函数
          var mW = 240;
          var mH = 240;
          var sX = 0;
          var sY = mH / 2;
          var axisLength = mW; //轴长
          var waveWidth = 0.04 ; //波浪宽度,数越小越宽
          var waveHeight = 12; //波浪高度,数越大越高
          ctx.save();
          ctx.translate(130,130);
          var points=[]; //用于存放绘制Sin曲线的点
          ctx.beginPath();
          //在整个轴长上取点
          for(var x = sX; x < sX + axisLength; x += 20 / axisLength){
            //此处坐标(x,y)的取点，依靠公式 “振幅高*sin(x*振幅宽 + 振幅偏移量)”
            var y = -Math.sin((sX + x) * waveWidth + xOffset);
            var dY = mH * (1 - nowRange / 100 );
            points.push([x, dY, dY + y * waveHeight]);
            ctx.lineTo(x, dY + y * waveHeight);
          }
          //封闭路径
          ctx.lineTo(axisLength, mH);
          ctx.lineTo(sX, mH);
          ctx.lineTo(points[0][0],points[0][1]);
          ctx.fillStyle = '#2C50B1';
          ctx.fill();

          ctx.restore();
        },
        drawText (ctx,nowRange){
          ctx.save();
          ctx.translate(130,130);
          var size = 50;
          ctx.font = size + 'px Microsoft Yahei';
          ctx.textAlign = 'center';
          ctx.fillStyle = "#95EFFF";
          ctx.fillText(nowRange + '%', 120, 120 - size/2 );


          ctx.restore();
          ctx.save()
          var size = 25;
          ctx.translate(130,130);
          ctx.font = size + 'px Microsoft Yahei';
          ctx.textAlign = 'center';
          ctx.fillStyle = "#95EFFF";
          ctx.fillText("平均任务完成率", 120, 120 + size );
          ctx.restore();
        },
        drawCircularText (s, string, startAngle, endAngle,n) {
          let context = $("#main").get(0).getContext('2d');
          var radius = s.radius,
            angleDecrement,
            angle = parseFloat(startAngle),
            index = 0,
            character;
          var arr = string.split(':')

          context.save();
          context.fillStyle = '#fff';
          context.font = '12px 微软雅黑 ';
          context.textAlign = 'center';
          context.textBaseline = 'middle';
          if (n<2 || n==5) {
            while(index < string.length) {
              character = string.charAt(index);
              if(arr[0].indexOf(character)>=0) {
                if (arr[0].length>6) {
                  angleDecrement = (startAngle - endAngle) / (string.length -3)
                }else {
                  angleDecrement = (startAngle - endAngle) / (string.length -1)
                }

              }else {
                angleDecrement = (startAngle - endAngle) / (string.length +6)
              }
              context.save();
              context.beginPath();
              context.translate(s.x + Math.cos(angle) * radius,
                s.y + Math.sin(angle) * radius);
              context.rotate(Math.PI / 2 + angle);
              context.fillText(character, 0, 0);
              angle -= angleDecrement;
              index++;
              context.restore();
            }
          } else {
            while(index < string.length) {
              character = string.split("").reverse().join("").charAt(index);// 字符串反转
              if(arr[1].indexOf(character)>=0) {
                angleDecrement = (startAngle - endAngle) / (string.length +6)
              }else {
                if (arr[0].length>6) {
                  angleDecrement = (startAngle - endAngle) / (string.length -3)
                }else {
                  angleDecrement = (startAngle - endAngle) / (string.length -1)
                }
              }
              context.save();
              context.beginPath();
              context.translate(s.x + Math.cos(angle) * radius,
                s.y + Math.sin(angle) * radius);
              context.rotate(-Math.PI/2 + angle);// 旋转文字
              context.fillText(character, 0, 0);
              angle -= angleDecrement;
              index++;
              context.restore();
            }
          }
          context.restore();
        },

      },
        mounted() {
          console.log(window.WIDGET)
          $("#main").height($(".circlePie").height())
          $("#main").width($(".circlePie").height())
          $("#dot").height($(".circlePie").height())
          $("#dot").width($(".circlePie").height())
          for (let i = 0; i < 200; i++) {

            let x = Math.random() *$(".circlePie").height();

            let y = Math.random() * $(".circlePie").height();

            let xa = Math.random() * 2 - 1;

            let ya = Math.random() * 2 - 1;




            this.dots.push({

              x: x,

              y: y,

              xa: xa,

              ya: ya,

              max: 60

            })

          }
          setTimeout(()=> {

            this.drawDot ();

          }, 1000);
          this.act();
          let _this = this;
            window.onresize = function () {
              $("#main").height($(".circlePie").height())
              $("#main").width($(".circlePie").height());
              $("#dot").height($(".circlePie").height())
              $("#dot").width($(".circlePie").height());
                // 通过捕获系统的onresize事件触发我们需要执行的事件
                // _this.$refs.chart1.setChart();
                // _this.$refs.chart2.setChart();
                // _this.$refs.channelBar1.setChart();
                // _this.$refs.distributionSolider1.setChart();
                // _this.$refs.channelBar2.setChart();
                // _this.$refs.distributionSolider2.setChart();
                // _this.$refs.pies.setPies();
                // _this.$refs.redPocket.setPocket();
                // _this.$refs.webcastsRisk.setWebcasts();
                // _this.$refs.deviceSafeRisk.setDeviceSafe();
                // _this.$refs.ring1.drawRing();
                // _this.$refs.ring2.drawRing();
                // _this.$refs.ring3.drawRing();
                // for (let i = 1; i < 9; i++) {
                //     _this.$refs['chart' + i].setChart()
                //
                // }
                _this.$refs.chinaMap.setMap();
                _this.$refs.hotWords.setChart();

            }

        },
    }
</script>

<style lang="less" scoped>
.chart-68 {
  width:68%;
  height:100%;
  float: left;
}

.chart-32 {
  width: 32%;
  height:100%;
  float: left;
}
    .mapList {
        height: 100%;
        width: 100%;
        padding: 10px 20px 20px;
        background: #03044A;

        .charts {
            height: 100%;

            .ivu-col {
                height: 100%;
                float: left;
            }

            .left, .right1-1, .center-bottom {
                height: 100%;
                border: 1px solid #0D2451;
                position: relative;
                background: #151456;

                #left_5 {
                    height: 100%;
                    width: 45%;
                    float: left;
                }

                #left_6 {
                    height: 100%;
                    width: 55%;
                    float: left;
                }

                .circular {
                    height: 100%;

                    .canvas {
                        height: 100%;
                        width: 30%;
                        float: left;

                        .subtitle {
                            font-size: 12px;
                            font-weight: bold;
                            color: #fff;
                            height: 25px;
                            padding: 10px 0 0 20px;
                        }

                        .canvasList {
                            height: calc(~'100% - 25px');
                            text-align: center
                        }
                    }

                    #right_3 {
                        height: 100%;
                        width: 70%;
                        float: right;
                    }
                }

                .left1 {
                    border-bottom: 1px solid #0D2451;
                    background: #151456;
                }

                .angle1 {
                    display: inline-block;
                    position: absolute;
                    width: 10px;
                    height: 10px;
                    top: 0;
                    left: 0;
                    border-top: 1px solid #1C5AB3;
                    border-left: 1px solid #1C5AB3;

                }

                .angle2 {
                    display: inline-block;
                    position: absolute;
                    width: 10px;
                    height: 10px;
                    top: 0;
                    right: 0;
                    border-top: 1px solid #1C5AB3;
                    border-right: 1px solid #1C5AB3;

                }

                .angle3 {
                    display: inline-block;
                    position: absolute;
                    width: 10px;
                    height: 10px;
                    bottom: 0;
                    left: 0;
                    border-bottom: 1px solid #1C5AB3;
                    border-left: 1px solid #1C5AB3;

                }

                .angle4 {
                    display: inline-block;
                    position: absolute;
                    width: 10px;
                    height: 10px;
                    bottom: 0;
                    right: 0;
                    border-bottom: 1px solid #1C5AB3;
                    border-right: 1px solid #1C5AB3;

                }
              .circlePie {
                height: 100%;
                padding:0 0 40px;
                text-align: center;
                position: relative;
                canvas {
                  position: absolute;
                  left: 50%;
                  top: 5%;
                  transform: translate(-50%,0);
                }
                #dot {
                  background: rgba(0,0,0,0);
                }
              }
                .title {
                    position: absolute;
                    display: inline-block;
                    color: #6EDDF1;
                    border: 2px solid #6EDDF1;
                    height: 18px;
                    padding: 0px 2px;
                    left: 50%;
                    transform: translate(-50%, -50%);

                    .title-text {
                        position: relative;
                        font-size: 16px;
                        background: #09102E;
                        display: inline-block;
                        padding: 0 4px;
                        margin-top: -5px;
                    }
                }
            }

            .center-top {
                height: 60%;

                #chinaMap {
                    height: 100%;
                }
            }

            .center-bottom {
                height: 40%;

                .bottom-radars {
                    height: 55%;
                }

                .bottom-bars {
                    height: 45%;
                }
            }

            .right-1 {
                height: 30%;

                .right1-1 {
                    height: 92%;
                }
            }

            .right-2 {
                height: 40%;

            }
        }
    }
    .logo{
      position: relative;
      left:100px;
      top:20px;
    }
</style>
