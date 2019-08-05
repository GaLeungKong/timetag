<template>
    <div>
        <!-- <div id="nav">
            <router-link to="/home">home</router-link> |
            <router-link to="/test">test</router-link>  
        </div> -->
        <el-tabs v-model="activeName">
            <el-tab-pane label="开始" name="start">
                <StartPanel />
            </el-tab-pane>
            <el-tab-pane label="统计" name="charts">
                <PieChart />
            </el-tab-pane>
        </el-tabs>
    </div>
</template>

<script>
// @ is an alias to /src
import StartPanel from '@/components/StartPanel.vue'
import PieChart from '@/components/PieChart.vue'

export default {
  components: {
    StartPanel,
    PieChart
  },
  data(){
      return{
          activeName:'start'
      }
  }
}
</script>