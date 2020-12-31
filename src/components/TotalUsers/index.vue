<template>
    <common-card title="累计用户数" value="1,532,221">
        <template>
            <div id="total-users" :style="{width:'100%',height:'100%'}"></div>
        </template>
        <template v-slot:footer>
            <div class="total-user-footer">
                <span>日同比 </span>
                <span class="emphasis">53.15%</span>
                <div class="increase" />
                <span class="month">月同比 </span>
                <span class="emphasis">91.44%</span>
                <div class="decrease" />
            </div>
        </template>
    </common-card>
</template>
<script>
    import CommonCardMixin from '../../mixins/commonCardMixin'
    export default {
        mixins: [CommonCardMixin],
        mounted () {
            const chartDom = document.getElementById('total-users')
            const chart = this.$echarts.init(chartDom)
            chart.setOption({
                grid: {
                    left: 0,
                    rigth: 0,
                    top: 0,
                    bottom: 0
                },
                xAxis: {
                    show: false,
                    boundaryGap: false
                },
                yAxis: {
                    type: 'category',
                    show: false
                },
                series: [{
                    type: 'bar',
                    data: [100],
                    barWidth: 10, // 柱状图每个柱子的宽度
                    itemStyle: {
                        color: '#45c946'
                    },
                    stack: '总量'
                }, {
                    type: 'bar',
                    data: [170],
                    barWidth: 10,
                    itemStyle: {
                        color: '#eee'
                    },
                    stack: '总量'// 数据堆叠，同个类目轴上系列配置相同的stack值可以叠放置
                }, {
                    type: 'custom',
                    data: [[100, 170]],
                    renderItem: function (params, api) {
                        const value = api.value(0)
                        const endPoint = api.coord([value, 0]) // coord() 将数值在当前坐标系中转换成为屏幕上的点的像素值
                        return {
                            type: 'group',
                            position: endPoint,
                            children: [
                                {
                                    type: 'path',
                                    shape: {
                                        d: 'M1024 255.996 511.971 767.909 0 255.996 1024 255.996z',
                                        x: -5,
                                        y: -20,
                                        width: 10,
                                        height: 10,
                                        layout: 'cover'
                                    },
                                    style: {
                                        fill: '#45c946'
                                    }
                                },
                                {
                                    type: 'path',
                                    shape: {
                                        d: 'M0 767.909l512.029-511.913L1024 767.909 0 767.909z',
                                        x: -5,
                                        y: 10,
                                        width: 10,
                                        height: 10,
                                        layout: 'cover'
                                    },
                                    style: {
                                        fill: '#45c946'
                                    }
                                }
                            ]
                        }
                    }
                }]
            })
        }
    }
</script>
<style lang="scss" scoped>
    .compare-wrapper {
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        .compare {
            display: flex;
            align-items: center;
            font-size: 12px;
            margin-top: 3px;
            color: #666;
        }
    }
    .total-user-footer {
        display: flex;
        align-items: center;
        .month {
            margin-left: 10px;
        }
    }
</style>
