<template>
    <div class="main">
        <svg class="guideLine" xmlns="http://www.w3.org/2000/svg" version="1.1" viewBox="0 30 783 500">
            <image x="5%" y="10" :xlink:href="$images.center" width="90%" height="100%" />
            <image v-if='!status' id="textBox" x="250" y="320" :xlink:href="$images.normal_bg" width="250" height="170" />
            <image v-else id="textBox_1" x="220" y="110" :xlink:href="$images.sensitive_bg" width="300" height="170" />
            <template>
                <g>
                    <image class="bg_img" x="85" y="354" :xlink:href="psychologicalStatus?$images.sensitive_title:$images.normal_title" width="130" height="50" />
                    <foreignObject class="title_1" x="102" y="364" id="title_1" width="100" height="40">
                        <div class="title-text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <p :style="{color:psychologicalStatus?'#FFDBDB':''}">
                                <span class="titleText">记忆障碍</span>
                                <Rate :show-text="false" disabled v-model="psychologicalRate"></Rate>
                            </p>
                        </div>
                    </foreignObject>
                    <foreignObject class="text" x="250" y="320" id="text_1" width="250" height="170">
                        <div class="text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <div class="promptBox">
                                <div class="promptTitle">记忆障碍</div>
                              <div>记忆障碍出现于早期，尤其是近记忆障碍，几十小时甚至数分钟前发生的事情都无法回忆</div>
                            </div>
                        </div>
                    </foreignObject>
                    <path id='line_1' class='swap swap1' d="M150,402 L150,432 250,432" stroke="#AFE5FB" stroke-width="2" fill="none" />
                </g>
                <g>
                    <image class="bg_img" x="58" y="224" :xlink:href="speechStatus?$images.sensitive_title:$images.normal_title"  width="130" height="50" />
                    <foreignObject class="title_1" x="76" y="232" id="title_2" width="100" height="40">
                        <div class="title-text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <p :style="{color:speechStatus?'#FFDBDB':''}">
                                <span class="titleText">语言障碍</span>
                                <Rate :show-text="false" disabled v-model="speechRate"></Rate>
                            </p>
                        </div>
                    </foreignObject>
                    <foreignObject class="text" x="250" y="320" id="text_2" width="250" height="170">
                        <div class="text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <div class="promptBox">
                                <div class="promptTitle">语言障碍</div>
                                <div>找词困难往往是老年痴呆症中最早出现的语言障碍，主要表现在说话时找不到合适的词语</div>
                            </div>
                        </div>
                    </foreignObject>
                    <path id='line_2' class='swap swap2' d="M125,272 L125,337 250,337" stroke="#AFE5FB" stroke-width="2" fill="none" />
                </g>
                <g>
                    <image class="bg_img" x="87" y="110" :xlink:href="internetPreferenceStatus?$images.sensitive_title:$images.normal_title"  width="130" height="50" />
                    <foreignObject class="title_1" x="105" y="118" id="title_3" width="100" height="40">
                        <div class="title-text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <p :style="{color:internetPreferenceStatus?'#FFDBDB':''}">
                                <span class="titleText">书写困难</span>
                                <Rate :show-text="false" disabled v-model="internetPreferenceRate">
                                </Rate>
                            </p>
                        </div>
                    </foreignObject>
                    <foreignObject class="text" x="250" y="320" id="text_3" width="250" height="170">
                        <div class="text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <div class="promptBox">
                                <div class="promptTitle">书写困难</div>
                                <div>因书写困难而导致写出的内容词不达意，如写信不能写清含义，这常常是引起家属注意的首发症状，特别是一些文化修养较好的老人</div>
                            </div>
                        </div>
                    </foreignObject>
                    <path id='line_3' class='swap swap3' d="M207,135 L260,135 260,322" stroke="#AFE5FB" stroke-width="2" fill="none" />
                </g>
                <g>
                    <image class="bg_img" x="310" y="40" :xlink:href="riskStatus?$images.sensitive_title:$images.normal_title"  width="130" height="50" />
                    <foreignObject class="title_1" x="328" y="49" id="title_4" width="100" height="40">
                        <div class="title-text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <p :style="{color:riskStatus?'#FFDBDB':''}">
                                <span class="titleText">失认和失用</span>
                                <Rate :show-text="false" disabled v-model="riskRate">
                                </Rate>
                            </p>
                        </div>
                    </foreignObject>
                    <foreignObject class="text" x="250" y="320" id="text_4" width="250" height="170">
                        <div class="text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <div class="promptBox">
                                <div class="promptTitle">失认和失用</div>
                                <div>失认是指病人不能辨认物体，尽管此时对物体的触觉或视觉要素都能辨认;失用是指虽有正常的活动能力与主观愿望，但不能执行已经学会的有目的的行动。</div>
                            </div>
                        </div>
                    </foreignObject>
                    <path id='line_4' class='swap swap4' d="M319,66 L279,66 279,321" stroke="#AFE5FB" stroke-width="2" fill="none" />
                </g>
                <g>
                    <image class="bg_img" x="530" y="110" :xlink:href="entertainmentPreferenceStatus?$images.sensitive_title:$images.normal_title"  width="130" height="50" />
                    <foreignObject class="title_1" x="538" y="118" id="title_5" width="120" height="40">
                        <div class="title-text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <p :style="{color:entertainmentPreferenceStatus?'#FFDBDB':''}">
                                <span style="font-size: 15px;display: block;">计算障碍</span>
                                <Rate :show-text="false" disabled v-model="entertainmentPreferenceRate" class="entertainment">
                                </Rate>
                            </p>
                        </div>
                    </foreignObject>
                    <foreignObject class="text" x="250" y="320" id="text_5" width="250" height="170">
                        <div class="text-box" xmlns="http://www.w3.org/1999/xhtml" >

                            <div class="promptBox">
                                <div class="promptTitle">计算障碍</div>
                                <div>计算障碍出现的原因有很多种，可能是由于视空间障碍(不能正确列算式)，或因失语不理解算术作业要求，也可能是原发性计算不能
                                </div>
                            </div>
                        </div>
                    </foreignObject>
                    <path id='line_5' class='swap swap3' d="M538,135 L485,135 485,322" stroke="#AFE5FB" stroke-width="2" fill="none" />
                </g>
                <g>
                    <image class="bg_img" x="560" y="224" :xlink:href="makeFriendStatus?$images.sensitive_title:$images.normal_title"  width="130" height="50" />
                    <foreignObject class="title_1" x="578" y="232" id="title_6" width="100" height="40">
                        <div class="title-text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <p :style="{color:makeFriendStatus?'#FFDBDB':''}">
                                <span class="titleText">判断力差</span>
                                <Rate :show-text="false" disabled v-model="makeFriendRate">
                                </Rate>
                            </p>
                        </div>
                    </foreignObject>
                    <foreignObject class="text" x="250" y="320" id="text_6" width="250" height="170">
                        <div class="text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <div class="promptBox">
                                <div class="promptTitle">判断力差</div>
                                <div>老年痴呆症患者均可在早期出现判断力差，概况能力丧失，注意力分散等</div>
                            </div>
                        </div>
                    </foreignObject>
                    <path id='line_6' class='swap swap2' d="M625,272 L625,337 500,337" stroke="#AFE5FB" stroke-width="2" fill="none" />
                </g>
                <g>
                    <image class="bg_img" x="538" y="354" :xlink:href="consumptionCharacteristicsStatus?$images.sensitive_title:$images.normal_title"  width="130" height="50" />
                    <foreignObject class="title_1" x="555" y="364" id="title_7" width="100" height="40">
                        <div class="title-text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <p :style="{color:consumptionCharacteristicsStatus?'#FFDBDB':''}">
                                <span class="titleText">精神障碍</span>
                                <Rate :show-text="false" disabled v-model="consumptionCharacteristicsRate">

                                </Rate>
                            </p>
                        </div>
                    </foreignObject>
                    <foreignObject class="text" x="250" y="320" id="text_7" width="250" height="170">
                        <div class="text-box" xmlns="http://www.w3.org/1999/xhtml" >
                            <div class="promptBox">
                                <div class="promptTitle">精神障碍</div>
                              <div>精神症状在早期可表现为患者以自我为中心，狂躁，幻觉妄想，抑郁，性格改变，谵妄等，情绪不易控制</div>
                            </div>
                        </div>
                    </foreignObject>
                    <path id='line_7' class='swap swap1' d="M600,402 L600,432 500,432" stroke="#AFE5FB" stroke-width="2" fill="none" />
                </g>
            </template>
        </svg>

    </div>
</template>

<script>
    import $ from 'jquery';
    export default {
        name: '',
        props:{
            selectRangeDate:Array,
            _width:Number
        },
        data() {
            return {
                psychology:'',
                showPsychology:true,
                psychologyPercent:'',
                speech:"",
                showSpeech:true,
                speechPercent:'',
                showBisexual:false,
                showViolate:false,
                showIdeology:false,
                risk:'',
                showRisk:true,
                riskPercent:'',
                existOutOfControl: false,
                existRoot: false,
                existViolations: false,
                makeFriend:'',
                showMakeFriend:true,
                makeFriendPercent:'',
                timer1:null,
                entertainmentPreference:'',
                showEntertainmentPreference:true,
                entertainmentPreferencePercent:'',
                entertainmentPreferenceContent:'',
                internetPreference:'',
                showInternetPreference:true,
                internetPreferencePercent:'',
                internetPreferenceUrl:[],
                consumptionCharacteristics:'',
                showConsumptionCharacteristics:true,
                consumptionCharacteristicsPercent:'',
                status:false,
                timer:null,
                rid:null,
                index:0,
                number:0,
                length:0,
                frames:0,
                isIE:false,
                psychologicalRate:0,
                speechRate:0,
                internetPreferenceRate:0,
                riskRate:0,
                makeFriendRate:0,
                entertainmentPreferenceRate:0,
                consumptionCharacteristicsRate:0,
                psychologicalStatus:false,
                speechStatus:false,
                internetPreferenceStatus:false,
                riskStatus:false,
                entertainmentPreferenceStatus:false,
                makeFriendStatus:false,
                consumptionCharacteristicsStatus:false,
                lineType:'psychological'
            }
        },
        methods: {
            frame() {
                cancelAnimationFrame(this.rid);
                this.rid = null;
                this.rid = requestAnimationFrame(this.frame);
                window["line_"+this.index].style.strokeDashoffset = this.frames;
                document.getElementById("line_"+this.index).getPointAtLength(this.length - this.frames);
                document.getElementById("line_"+this.index).getPointAtLength((this.length - this.frames + 2) % this.length);
                if (this.index>1) {
                    $("#text_"+(this.index-1)).css('opacity',0)
                    window[("line_"+(this.index-1))].style.strokeDashoffset=window[("line_"+(this.index-1))].style.strokeDasharray;
                }
                if (this.index==1) {
                    for (let i = 2; i < 8; i++){
                        $("#text_"+i).css('opacity',0);
                        window[("line_"+i)].style.strokeDashoffset=window[("line_"+i)].style.strokeDasharray;

                    }
                }
                $("#text_"+this.index).css('opacity',this.number);
                $("#textBox").css('opacity',this.number);
                this.number+=5/this.length;
                this.frames-=5;
                if (this.frames <=-5) {
                    cancelAnimationFrame( this.rid);
                    this.rid = null;
                }
            },
            animation (i,boolean) {
                clearTimeout(this.timer);
                cancelAnimationFrame( this.rid);
                this.rid = null;
                this.timer = null;
                if (i >7) {
                    i=1;
                }
                this.psychologicalStatus =false;
                this.speechStatus=false
                this.internetPreferenceStatus=false
                this.riskStatus=false
                this.entertainmentPreferenceStatus=false
                this.makeFriendStatus=false
                this.consumptionCharacteristicsStatus=false
                switch (i) {
                    case 1:
                        this.psychologicalStatus =true;
                        this.lineType = 'psychological'
                        break;
                    case 2:
                        this.speechStatus =true;
                        this.lineType = 'speech'
                        break;
                    case 3:
                        this.internetPreferenceStatus =true;
                        this.lineType = 'internet'
                        break;
                    case 4:
                        this.riskStatus =true;
                        this.lineType = 'risk'
                        break;
                    case 5:
                        this.entertainmentPreferenceStatus =true;
                        this.lineType = 'entertainment'
                        break;
                    case 6:
                        this.makeFriendStatus =true;
                        this.lineType = 'social'
                        break;
                    case 7:
                        this.consumptionCharacteristicsStatus =true;
                        this.lineType = 'consumption'
                        break;
                    default:
                        break
                }
                this.length = window["line_"+i].getTotalLength();
                this.length = document.getElementById("line_"+i).getTotalLength();
                document.getElementById("line_"+i).style.strokeDasharray = this.length;
                document.getElementById("line_"+i).style.strokeDashoffset = this.length;
                this.frames = this.length;
                this.index=i;
                this.number = 0;
                this.frame();
                if (boolean) {
                    return
                }else {
                    clearTimeout(this.timer);
                    this.timer = null;
                    this.timer = setTimeout(() => {
                        this.animation(i+1,boolean);
                    }, 5000);
                }
            },
            // 中心图
            setChart () {
                clearTimeout(this.timer1);
                clearTimeout(this.timer);
                cancelAnimationFrame(this.rid);
                this.frames =0;
                this.rid = null;
                this.timer = null;
                this.timer1=null
                this.timer1 =  setTimeout(() => {
                    this.animation(1,false);
                }, 10000);

            }
        },
        watch:{
            selectRangeDate:function () {
                this.setChart()
            }
        },
        created() {
            if (!window.SVGForeignObjectElement) {
                this.isIE = true;
            }
        },
        destroyed() { // 离开页面动画初始化
            $(".text").css('opacity',0);
            $(".swap1").css('strokeDashoffset',130);
            $(".swap2").css('strokeDashoffset',190);
            $(".swap3").css('strokeDashoffset',240);
            $(".swap4").css('strokeDashoffset',295);
            cancelAnimationFrame( this.rid);
            this.rid = null;
            clearTimeout(this.timer)
            clearTimeout(this.timer1)
            this.timer = null;
            this.timer1 = null;
            this.psychologicalStatus =false;
            this.speechStatus=false
            this.internetPreferenceStatus=false
            this.riskStatus=false
            this.entertainmentPreferenceStatus=false
            this.makeFriendStatus=false
            this.consumptionCharacteristicsStatus=false
        },
        mounted() {
            this.setChart();
            let _this = this;
            $(".title_1").mouseenter(function (e) {
                $(".text").css('opacity', 0);
                $(".swap1").css('strokeDashoffset', 130);
                $(".swap2").css('strokeDashoffset', 190);
                $(".swap3").css('strokeDashoffset', 240);
                $(".swap4").css('strokeDashoffset', 295);
                cancelAnimationFrame(_this.rid);
                _this.rid = null;
                clearTimeout(_this.timer)
                clearTimeout(_this.timer1)
                _this.timer = null;
                _this.timer1 = null;
                _this.animation(Number(e.currentTarget.id.substr(e.currentTarget.id.length - 1, 1)), true);
            });
            $(".title_1").mouseleave(function () {
                _this.animation(1, false);

            });

        }
    }
</script>


<style lang="less">
    .main {
        width:100%;
        height:100%;
        position: relative;
        .href {
            position: absolute;
            right: 20px;
            top: 30px;
            color: #00C0FF;
            z-index: 2;
            cursor: pointer;
        }
        .guideLine {
            width: 100%;
            height: 100%;
            #textBox {
                opacity: 0;
            }
            #textBox_1 {
                opacity: 0;
            }
            .title_1 {
                font-size: 15px;
                cursor: pointer;
                .title-text-box {
                    background:rgba(0,0,0,0);
                    justify-content:center;//子元素水平居中
                    align-items:center;//子元素垂直居中
                    display:-webkit-flex;
                    height: 100%;
                    p {
                        width: 100%;
                        background: rgba(0,0,0,0);
                        color:#A0E8FF;
                        font-size:  15px;
                        text-align:center;
                        .titleText {
                            margin-left: -5px;
                            font-size: 15px;
                            display: block;
                        }
                        .ivu-rate {
                            font-size: 14px;
                            .ivu-rate-star {
                                margin-right: 6px;
                            }
                        }

                    }
                }
            }
            .text {
                opacity: 0;
                color:#fff;
                font-size: 15px;
                text-align:center;
                .text-box {
                    background:rgba(0,0,0,0);
                    justify-content:center;//子元素水平居中
                    align-items:center;//子元素垂直居中
                    display:-webkit-flex;
                    .promptBox {
                        width: 100%;
                        height: 100%;
                        padding: 10px 20px;
                        .promptTitle {
                            color:#fff;
                            font-size: 16px;
                            font-weight: bold;
                            margin-bottom: 5px;
                        }
                        p {
                            background: rgba(0,0,0,0);
                            color:#A0E8FF;
                            font-size: 16px;
                            text-align:left;
                        }
                    }
                    .psychologyContent {
                        color:#AFE5FB;
                        font-size: 16px;
                        text-align:left;
                        div {
                            line-height: 2em;
                            span {
                                &:first-child {
                                    color: #FED723;
                                    cursor: pointer;
                                }
                            }
                        }
                    }

                }
            }
            .swap1 {
                stroke-dasharray: 130;
                stroke-dashoffset: 130;
            }
            .swap2 {
                stroke-dasharray: 190;
                stroke-dashoffset:190;
            }
            .swap3 {
                stroke-dasharray: 240;
                stroke-dashoffset: 240;
            }
            .swap4 {
                stroke-dasharray: 295;
                stroke-dashoffset: 295;
            }
            .circle-point {
                &:hover {
                    fill: #000;
                }
            }
            // .swap4{
            // stroke-dasharray: 110;
            // stroke-dashoffset: 110;
            // }
        }
    }
</style>
