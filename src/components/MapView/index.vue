<template>
    <div class="map-view">
        <div class="left">
            <b-map-scatter />
        </div>
        <div class="right">456</div>
    </div>
</template>

<script>
import BMapScatter from '../BMapScatter'
export default {
    components: {
        BMapScatter
    }
}
</script>

<style lang="scss" scoped>
    .map-view {
        display: flex;
        margin-top: 20px;
        .left {
            flex: 0 0 80%;
            width: 80%;
            height: 600px;
        }
        .right {
            flex: 1;
            display: flex;
        }
    }
</style>
