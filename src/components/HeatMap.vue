<template>
  <div>
    <el-link :underline="false"><i class="el-icon-refresh-left"></i>refresh</el-link>
    <div id="main" style="width: 1080px;height:960px;"></div>
  </div>
</template>

<script>
export default {
  name: "HeatMap",
  data(){
      return {
        option:{}
      }
  },
  methods: {
    // getFormatDate(d){
    //     let currentYear = d.getFullYear().toString()
    //     let currentMonth = d.getMonth() + 1
    //     currentMonth = currentMonth > 10 ? ('0' + currentMonth) : currentMonth 
    //     let currentDate = d.getDate()
    //     currentDate = currentDate > 10 ? ('0' + currentDate) : currentDate
    //     let current = currentYear + '-' + currentMonth + '-' + currentDate
    //     return current
    // },
    getdata(){
        let data = []  
        // let formList = JSON.parse(window.localStorage.getItem('dataStore') || '[]');
        // // if(formList.length != 0){
        // //   let currentDate =this.getFormatDate(formList[0].date)
        // // }
        // let count = 0
        // for(let i=0;i<form.length;i++){
        //     if(form.label === '学习' || form.label === '工作' || form.label === '工作'){
        //        formList[i].date
        //     }
        // }
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
                left: '300',
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
