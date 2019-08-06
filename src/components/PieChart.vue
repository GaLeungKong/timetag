<template>
  <div>
      <div id="main" style="width: 1080px;height:960px;"></div>
  </div>
</template>

<script>
export default {
  name: "PieChart",
  data(){
      return {
        option:{}
      }
  },
  methods: {
    getdata(){
        var data = []
        
        let formList = JSON.parse(window.localStorage.getItem('dataStore') || '[]');
        return data
    },
    getOption(){
        this.option={
            tooltip: {
                position: 'top',
                formatter: function (p) {
                    var format = echarts.format.formatTime('yyyy-MM-dd', p.data[0]);
                    return format + ': ' + p.data[1];
                }
            },
            visualMap: {
                min: 0,
                max: 24,
                calculable: true,
                orient: 'vertical',
                left: '400',
                top: 'center'
            },
            calendar: [
            {
                cellSize: [20, 'auto'],
                bottom: 0,
                orient: 'vertical',
                range: '2019'
            }],
            series: [{
                type: 'heatmap',
                coordinateSystem: 'calendar',
                calendarIndex: 0,
                data: this.getdata()
            }]            
        }

    },
    drawChart() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("main"));
      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(this.option);
    }
  },
  mounted() {
    this.getOption();
    this.drawChart();
  },
};
</script>
