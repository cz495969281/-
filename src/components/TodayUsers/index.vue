<template>
    <common-card title="今日交易用户数" value="544,894">
        <template>
            <div id="today-jiaoyi" :style="{width:'100%',height:'100%'}"></div>
        </template>
        <template v-slot:footer>
            <span>退货率  </span>
            <span class="emphasis">5.24%</span>
        </template>
    </common-card>
</template>
<script>
    import CommonCardMixin from '../../mixins/commonCardMixin'
    export default {
        mixins: [CommonCardMixin],
        mounted () {
            const chartDom = document.getElementById('today-jiaoyi')
            const chart = this.$echarts.init(chartDom)
            chart.setOption({
                color: ['#3398DB'],
                xAxis: {
                    type: 'category',
                    show: false,
                    data: ['00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00']
                },
                yAxis: {
                    show: false
                },
                series: [
                    {
                        type: 'bar',
                        data: [140, 432, 220, 300, 200, 430, 180, 450, 150, 200, 430, 180, 450],
                        barWidth: '60%' // 柱状图的宽度
                    }
                ],
                grid: {
                    top: 0,
                    bottom: 0,
                    left: 0,
                    right: 0
                }
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
</style>
