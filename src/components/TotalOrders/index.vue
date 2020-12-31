<template>
    <common-card title="累计订单量" value="3,066,427">
        <template>
            <v-chart :options="getOptions()" />
        </template>
        <template v-slot:footer>
            <span>昨日订单量  </span>
            <span class="emphasis">2,000,000</span>
        </template>
    </common-card>
</template>
<script>
    import CommonCardMixin from '../../mixins/commonCardMixin'
    export default {
        mixins: [CommonCardMixin],
        methods: {
            getOptions () {
                return {
                    xAxis: {
                        type: 'category',
                        show: false,
                        boundaryGap: false
                    },
                    yAxis: {
                        show: false
                    },
                    series: [
                        {
                            type: 'line',
                            data: [200, 432, 220, 400, 380, 430, 330, 450, 150],
                            areaStyle: {
                                color: 'purple'
                            },
                            lineStyle: {
                                width: 0
                            },
                            itemStyle: {
                                opacity: 0
                            },
                            smooth: true
                        }
                    ],
                    grid: {
                        top: 0,
                        bottom: 0,
                        left: 0,
                        right: 0
                    }
                }
            }
        }
    }
</script>
<style lang="scss" scoped>
    // .compare-wrapper {
    //     height: 100%;
    //     display: flex;
    //     flex-direction: column;
    //     justify-content: center;
    //     .compare {
    //         display: flex;
    //         align-items: center;
    //         font-size: 12px;
    //         margin-top: 3px;
    //         color: #666;
    //     }
    // }
</style>
