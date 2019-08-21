<template>
    <div>
        <div>
            <p>某日</p>
            <el-date-picker
                v-model="selectedDate"
                align="right"
                type="date"
                placeholder="选择日期"
                :picker-options="datePickerOptions">
            </el-date-picker>
            <el-button type="primary" @click="chartQuery(selectedDate,'dateQuery')">确定</el-button>
            
        </div>
        <el-divider></el-divider>
        <div>
            <p>某周</p>
            <el-date-picker
                v-model="selectedWeek"
                type="week"
                format="yyyy 第 WW 周"
                placeholder="选择周">
            </el-date-picker>
            <el-button type="primary"  @click="chartQuery(selectedWeek,'weekQuery')">确定</el-button>
        </div>
        <el-divider></el-divider>
        <div>
            <p>某月</p>
            <el-date-picker
                v-model="selectedMonth"
                type="month"
                placeholder="选择月">
            </el-date-picker>
            <el-button type="primary" @click="chartQuery(selectedMonth,'monthQuery')">确定</el-button>
        </div>
        <el-divider></el-divider>
        <div>
            <p>某年</p>
            <el-date-picker
                v-model="selectedYear"
                type="year"
                placeholder="选择年">
            </el-date-picker>
            <el-button type="primary" @click="chartQuery(selectedYear,'yearQuery')">确定</el-button>
        </div>

    </div>
</template>

<script>
export default {
    data(){
        return{
            datePickerOptions: {
                disabledDate(time) {
                    return time.getTime() > Date.now();
                },
                shortcuts: [{
                    text: '今天',
                    onClick(picker) {
                    picker.$emit('pick', new Date());
                    }
                }, {
                    text: '昨天',
                    onClick(picker) {
                    const date = new Date();
                    date.setTime(date.getTime() - 3600 * 1000 * 24);
                    picker.$emit('pick', date);
                    }
                }, {
                    text: '一周前',
                    onClick(picker) {
                    const date = new Date();
                    date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
                    picker.$emit('pick', date);
                    }
                }]
            },
            
            selectedDate:'',
            selectedWeek:'',
            selectedMonth:'',
            selectedYear:'',
        }
    },
    methods:{
        chartQuery(date,type){
            if(date === null || date === '')alert("请先选择要查询的时间段")
            else this.$router.push('/dateCharts')
        }

    }
}
</script>

<style scope>
    .el-button{
        margin: 5px;
    }
</style>