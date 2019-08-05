<template>
  <div class="hello">
    <el-row class="test" v-for="(card, index) in cards"> 
      <el-col :span="12" :offset=6>
          <el-card>
            <el-button @click="eventStart(index)">{{card}}</el-button>
          </el-card>
        </el-card>
      </el-col>
    </el-row>

    <el-dialog title="具体内容" :visible.sync="dialogFormVisible">
      <el-form :model="form">
        <el-form-item label="内容名称" :label-width="formLabelWidth">
          <el-input v-model="form.name" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="补充" :label-width="formLabelWidth">
          <el-input type="textarea" v-model="form.statement" placeholder="" :autosize="{minRows:2, maxRows:4}"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="textConfirm">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>

export default {
  name: 'StartPanel',
  props: {
    msg: String
  },
  data(){
    return{
      selectedEvent:0,
      cards:['学习','休息','内务/三餐','读书/写作','电影/剧','游戏','运动','浪费/发呆/忘了','外出'],
      dialogFormVisible: false,
       form: {
          label:'',
          name: '',
          statement: '',
          date: '',
        },
        formLabelWidth: '120px',
    }
  },
  methods:{
    showAlert(){
      alert("testing")
    },
    eventStart(val){
      this.dialogFormVisible = true
      this.selectedEvent = val
      this.form.label = this.cards[this.selectedEvent];

    },
    textConfirm(){
      this.form.date = new Date().toString();
      this.dialogFormVisible = false;

      let obj = {};
      obj.label = this.form.label
      obj.name = this.form.name
      obj.statement = this.form.statement
      obj.date = this.form.date

      let formList = JSON.parse(window.localStorage.getItem('dataStore') || '[]');
      formList.push(obj);
      window.localStorage.setItem('dataStore',JSON.stringify(formList));
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.el-row{
  margin: 20px;
    
}
.test{
  margin-top: 20px;
}
.el-card{
  margin: 0 auto;
}
</style>
