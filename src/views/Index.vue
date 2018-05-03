<template>
    <section class="chart-container">
        <el-row style="margin-top: 20px">
            <div class="welinfo">
                <span><img src="http://demo.cssmoban.com/cssthemes4/zwtp_2_gi/images/sun.png" alt="天气"/></span>
                <b>Admin，欢迎使用XXX后台管理平台</b>
            </div>

            <div class="welinfo">
                <span><img src="http://demo.cssmoban.com/cssthemes4/zwtp_2_gi/images/time.png" alt="时间"/></span>
                <i>您上次登录的时间：2018-10-10 15:22</i>
            </div>

            <div class="xline"></div>

        </el-row>

        <el-row>
            <el-col :span="12">
                <div id="chartLine" style="width:100%; height:400px;"></div>
            </el-col>
            <el-col :span="12">
                <div id="chartPie" style="width:100%; height:400px;"></div>
            </el-col>
        </el-row>
    </section>
</template>

<script>
    import echarts from 'echarts'

    export default {
        data() {
            return {
                chartColumn: null,
                chartBar: null,
                chartLine: null,
                chartPie: null
            }
        },

        methods: {
            drawLineChart() {
                this.chartLine = echarts.init(document.getElementById('chartLine'));
                this.chartLine.setOption({
                    title: {
                        text: '近七天用户活跃度',
                    },
                    tooltip: {
                        trigger: 'axis'
                    },
                    legend: {
                        data: ['用户活跃度']
                    },
                    grid: {
                        left: '3%',
                        right: '4%',
                        bottom: '3%',
                        containLabel: true
                    },
                    xAxis: {
                        type: 'category',
                        boundaryGap: false,
                        data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
                    },
                    yAxis: {
                        type: 'value'
                    },
                    series: [
                        {
                            name: '用户活跃度',
                            type: 'line',
                            stack: '总量',
                            data: [120, 132, 101, 134, 90, 230, 210]
                        }
                    ],
                    color:['#72bff3']
                });
            },
            drawPieChart() {
                this.chartPie = echarts.init(document.getElementById('chartPie'));
                this.chartPie.setOption({
                    title: {
                        text: '热度排行榜',
                        subtext: '截止2018-10-10',
                        x: 'center'
                    },
                    tooltip: {
                        trigger: 'item',
                        formatter: "{a} <br/>{b} : {c} ({d}%)"
                    },
                    legend: {
                        orient: 'vertical',
                        left: 'left',
                        data: ['上海教育', '成长发育', '才艺启蒙', '科学育儿', '各地要闻']
                    },
                    series: [
                        {
                            name: '访问来源',
                            type: 'pie',
                            radius: '55%',
                            center: ['50%', '60%'],
                            data: [
                                {value: 335, name: '上海教育'},
                                {value: 310, name: '成长发育'},
                                {value: 234, name: '才艺启蒙'},
                                {value: 135, name: '科学育儿'},
                                {value: 1548, name: '各地要闻'}
                            ],
                            itemStyle: {
                                emphasis: {
                                    shadowBlur: 10,
                                    shadowOffsetX: 0,
                                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                                }
                            }
                        }
                    ],
                    color:['#72bff3','#33ff2e', '#44ff5c', '#31cbff','#ff8687','#33332e','#72a0ff']
                });
            },
            drawCharts() {
                this.drawLineChart()
                this.drawPieChart()
            },
        },

        mounted: function () {
            this.drawCharts()
        },
        updated: function () {
            this.drawCharts()
        }
    }
</script>

<style scoped>
    /*index*/
    .welinfo {
        height: 32px;
        padding-bottom: 8px;
    }

    .welinfo span {
        float: left;
    }

    .welinfo b {
        padding-left: 8px;
        line-height: 32px;
    }

    .welinfo a {
        padding-left: 15px;
        color: #3186c8;
    }

    .welinfo a:hover {
        color: #F60;
    }

    .welinfo i {
        font-style: normal;
        padding-left: 8px;
        line-height: 32px;
    }

    .xline{border-bottom:solid 1px #dfe9ee; height:5px;}

    .chart-container {
        width: 100%;
        float: left;
    }

    /*.chart div {
        height: 400px;
        float: left;
    }*/

    .el-col {
        padding: 30px 20px;
    }
</style>
