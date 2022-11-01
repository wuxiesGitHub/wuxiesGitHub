- 👋 Hi, I’m @wuxiesGitHub
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
wuxiesGitHub/wuxiesGitHub is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="en" style=" width: 100%;
    height: 100%;
    background-color: #010d3a;">
<head>
    <meta charset="UTF-8">
    <title>大学生软件设计大赛芯片质检</title>
    <!-- 引入 echarts.js -->
    <script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.js"></script>
    <script src="https://cdn.staticfile.org/echarts/4.5.0/echarts.min.js"></script>
    <script type="text/javascript" src="./js/timeouttask.js"></script>

<body>

<!--滚动条div块-->
<font style="font-size: 142%; color: #47d8ff; position: relative;  left: 1133px;  top: 28px;" >历史发布信息</font>
<div style="position: relative;left:949px;top: 15px;width: 77px;height: 87px; color:#47d8ff">
    <tbody>
    <tr>
        <td bgcolor="#f8f8e5" style="color: #010d3a">
            <!--width 滚动条宽度   height 滚动条高度   -->
            <marquee   width="450"  height="200" direction="down"  hspace="40"  vspace="40" scrollamount="3">滚动文字111111111111111111111111111111111111111111111111111111111111111111111111111 滚动文字滚动文字滚动文字滚动文字滚动文字滚动文字</marquee>
        </td>
    </tr>
    </tbody>
</div>

<!--芯片质检分数-->
<div style="position: relative;left:949px;top: 15px;width: 77px;height: 87px;">
    <div style="width: 260px">
    <font style="font-size: 200%;  position: relative;  left: 50px;  top: 175px;color:#47d8ff" >芯片质检分数</font>
    </div>
<!-- id就是js的getid      var myChart = echarts.init(document.getElementById('main'));-->
    <div id="main" style="position: absolute;     left: -171px;  top: 180px; width: 676px; height: 360px;  user-select: none;  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);  padding: 0px;   margin: 0px; border-width: 0px;"></div>
</div>

<!--芯片总数量-->
<div>
    <font style="font-size: 176%; position: relative; left: 86px; top: -181px;color: #47d8ff;color:#47d8ff" >芯片总数</font>
    <div id="AlertTaskJSs"  style=" position: absolute;left:-109px;top: 23px;width: 516px;height: 274px;user-select: none;-webkit-tap-highlight-color: transparent;padding: 0px; margin: 0px;   border-width: 0px;"></div>
</div>

<!--引脚缺失-->
<div>
    <font style="    font-size: 176%; position: relative;  left: 435px; top: -217px;color:#47d8ff" >引脚缺失</font>
    <div  id="ExecutetaskJS"  style=" position: absolute;left: 240px; top: 22px;;width: 516px;height: 274px;user-select: none;-webkit-tap-highlight-color: transparent;padding: 0px; margin: 0px;   border-width: 0px;"></div>
</div>

<!--划痕-->
<div>
    <font style="font-size: 176%;position: relative;left: 750px;top: -254px;color: #47d8ff;" >划痕出现</font>
    <div id="timeOutTaskJS"  style="position: absolute;left: 555px; top: 22px;width: 516px;height: 274px;user-select: none;-webkit-tap-highlight-color: transparent;padding: 0px; margin: 0px;   border-width: 0px;"></div>
</div>


<!--芯片质检合格率-->
<font style="font-size: 200%;  position: relative;  left: 237px; top: -5px;color:#47d8ff" >芯片质检合格率</font>
    <div id="numberOfElderly"  style="position: absolute;left: 89px; top: 371px;  width: 586px; height: 305px;user-select: none;-webkit-tap-highlight-color: transparent;padding: 0px; margin: 0px;   border-width: 0px;"></div>
</body>


<!--芯片质检分数js-->
<script>
    var myChart = echarts.init(document.getElementById('main'));

    const CubeLeft = echarts.graphic.extendShape({
        shape: {
            x: 20,
            y: 10
        },
        buildPath: function(ctx, shape) {
            const xAxisPoint = shape.xAxisPoint
            const c0 = [shape.x, shape.y]
            const c1 = [shape.x - 9, shape.y - 9]
            const c2 = [xAxisPoint[0] - 9, xAxisPoint[1] - 9]
            const c3 = [xAxisPoint[0], xAxisPoint[1]]
            ctx.moveTo(c0[0], c0[1]).lineTo(c1[0], c1[1]).lineTo(c2[0], c2[1]).lineTo(c3[0], c3[1]).closePath()
        }
    })
    const CubeRight = echarts.graphic.extendShape({
        shape: {
            x: 10,
            y: 10
        },
        buildPath: function(ctx, shape) {
            const xAxisPoint = shape.xAxisPoint
            const c1 = [shape.x, shape.y]
            const c2 = [xAxisPoint[0], xAxisPoint[1]]
            const c3 = [xAxisPoint[0] + 18, xAxisPoint[1] - 9]
            const c4 = [shape.x + 18, shape.y - 9]
            ctx.moveTo(c1[0], c1[1]).lineTo(c2[0], c2[1]).lineTo(c3[0], c3[1]).lineTo(c4[0], c4[1]).closePath()
        }
    })
    const CubeTop = echarts.graphic.extendShape({
        shape: {
            x: 0,
            y: 0
        },
        buildPath: function(ctx, shape) {
            const c1 = [shape.x, shape.y]
            const c2 = [shape.x + 18, shape.y - 9]
            const c3 = [shape.x + 9, shape.y - 18]
            const c4 = [shape.x - 9, shape.y - 9]
            ctx.moveTo(c1[0], c1[1]).lineTo(c2[0], c2[1]).lineTo(c3[0], c3[1]).lineTo(c4[0], c4[1]).closePath()
        }
    })
    echarts.graphic.registerShape('CubeLeft', CubeLeft)
    echarts.graphic.registerShape('CubeRight', CubeRight)
    echarts.graphic.registerShape('CubeTop', CubeTop)
    const MAX = [6000, 6000, 6000, 6000, 6000, 5000, 4000, 3000, 2000, 4000, 3000, 2000]
    const VALUE = [2012, 1230, 3790, 2349, 1654, 1230, 3790, 2349, 1654, 3790, 2349, 1654]
    option = {
        // backgroundColor: "#010d3a",
        title: {
            text: '',
            top: 32,
            left: 18,
            textStyle: {
                color: '#00F6FF',
                fontSize: 24
            }
        },
        /*调整表格大小*/
        grid: {
            left: 0,
            right: 0,
            bottom: '6%',
            top: 90,
            containLabel: true
        },
        xAxis: {
            type: 'category',
            data: ['第一次', '第二次', '第三次', '第四次', '第五次', '第六次',
                '第七次', '第八次', '第九次', '第十次', '第十一次', '第十二次'
            ],
            axisLine: {
                show: true,
                lineStyle: {
                    color: 'white'
                }
            },
            offset: 20,
            axisTick: {
                show: false,
                length: 9,
                alignWithLabel: true,
                lineStyle: {
                    color: '#7DFFFD'
                }
            },
            axisLabel: {
                fontSize: 10
            }
        },
        yAxis: {
            type: 'value',
            axisLine: {
                show: true,
                lineStyle: {
                    color: 'white'
                }
            },
            splitLine: {
                show: false
            },
            axisTick: {
                show: false
            },
            axisLabel: {
                fontSize: 16
            },
            boundaryGap: ['20%', '20%']
        },
        series: [{
            type: 'custom',
            renderItem: function(params, api) {
                const location = api.coord([api.value(0), api.value(1)])
                return {
                    type: 'group',
                    children: [{
                        type: 'CubeLeft',
                        shape: {
                            api,
                            xValue: api.value(0),
                            yValue: api.value(1),
                            x: location[0],
                            y: location[1],
                            xAxisPoint: api.coord([api.value(0), 0])
                        },
                        style: {
                            fill: 'rgba(7,29,97,.6)'
                        }
                    }, {
                        type: 'CubeRight',
                        shape: {
                            api,
                            xValue: api.value(0),
                            yValue: api.value(1),
                            x: location[0],
                            y: location[1],
                            xAxisPoint: api.coord([api.value(0), 0])
                        },
                        style: {
                            fill: 'rgba(10,35,108,.7)'
                        }
                    }, {
                        type: 'CubeTop',
                        shape: {
                            api,
                            xValue: api.value(0),
                            yValue: api.value(1),
                            x: location[0],
                            y: location[1],
                            xAxisPoint: api.coord([api.value(0), 0])
                        },
                        style: {
                            fill: 'rgba(11,42,106,.8)'
                        }
                    }]
                }
            },
            data: MAX
        }, {
            type: 'custom',
            renderItem: (params, api) => {
            const location = api.coord([api.value(0), api.value(1)])
            return {
                type: 'group',
                children: [{
                    type: 'CubeLeft',
                    shape: {
                        api,
                        xValue: api.value(0),
                        yValue: api.value(1),
                        x: location[0],
                        y: location[1],
                        xAxisPoint: api.coord([api.value(0), 0])
                    },
                    style: {
                        fill: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                            offset: 0,
                            color: '#3B80E2'
                        },
                            {
                                offset: 1,
                                color: '#49BEE5'
                            }
                        ])
                    }
                }, {
                    type: 'CubeRight',
                    shape: {
                        api,
                        xValue: api.value(0),
                        yValue: api.value(1),
                        x: location[0],
                        y: location[1],
                        xAxisPoint: api.coord([api.value(0), 0])
                    },
                    style: {
                        fill: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                            offset: 0,
                            color: '#3B80E2'
                        },
                            {
                                offset: 1,
                                color: '#49BEE5'
                            }
                        ])
                    }
                }, {
                    type: 'CubeTop',
                    shape: {
                        api,
                        xValue: api.value(0),
                        yValue: api.value(1),
                        x: location[0],
                        y: location[1],
                        xAxisPoint: api.coord([api.value(0), 0])
                    },
                    style: {
                        fill: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                            offset: 0,
                            color: '#3B80E2'
                        },
                            {
                                offset: 1,
                                color: '#49BEE5'
                            }
                        ])
                    }
                }]
            }
        },
            data: VALUE
    }, {
        type: 'bar',
            label: {
            normal: {
                show: true,
                    position: 'top',
                    formatter: (e) => {
                    switch (e.name) {
                        case '10kV线路':
                            return VALUE[0]
                        case '公用配变':
                            return VALUE[1]
                        case '35kV主变':
                            return VALUE[2]
                        case '水':

                    }
                },
                fontSize: 16,
                    color: '#38ff9f',
                    offset: [4, -25]
            }
        },
        itemStyle: {
            color: 'transparent'
        },
        data: MAX
    }]
    }

    myChart.setOption(option);
</script>
