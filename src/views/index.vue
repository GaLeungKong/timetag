<template>
    <div>
        <el-tabs v-model="activeName">
            <el-tab-pane label="开始" name="start">
                <StartPanel />
            </el-tab-pane>
            <el-tab-pane label="统计" name="charts">
                <el-row>
                    <el-col :span='12'><DateSelector /></el-col>
                    <el-col :span='12'><HeatMap /></el-col>
                </el-row>
            </el-tab-pane>
        </el-tabs>
    </div>
</template>

<script>
// @ is an alias to /src
import StartPanel from '@/components/StartPanel.vue'
import HeatMap from '@/components/HeatMap.vue'
import DateSelector from '../components/DateSelector.vue';

export default {
  components: {
    StartPanel,
    HeatMap,
    DateSelector
  },
  data(){
      return{
          activeName:'start'
      }
  }
}
</script>