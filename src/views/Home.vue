<template>
  <div class="home">
    <el-menu mode="horizontal">
      <el-menu-item index="1">开始</el-menu-item>
      <el-menu-item index="2">记录</el-menu-item>
    </el-menu>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  }
}
</script>
