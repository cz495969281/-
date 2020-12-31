<template>
  <div class='home'>
    <top-view></top-view>
    <sales-view></sales-view>
  </div>
</template>

<script>
import TopView from '../components/TopView'
import SalesView from '../components/SalesView'
export default {
  name: 'Home',
  components: {
    TopView,
    SalesView
  }
}
</script>
<style>
.home {
  width: 100%;
  padding: 20px;
  background: #eee;
  box-sizing: border-box;
}
</style>
