<template>
  <div class="hello">
    <el-timeline>
      <el-timeline-item timestamp="2018/4/12" placement="top">
      </el-timeline-item> 
    </el-timeline>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  data(){
    return
  },
  created(){
    axios.get('../assets/passage.json')
    .then(Response)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
