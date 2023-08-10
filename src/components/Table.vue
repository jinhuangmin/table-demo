

<template>
 
 <el-button type="primary"  @click="centerDialogVisible = true">
    新增
  </el-button>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="name" label="名称" width="180" />
    <el-table-column prop="age" label="年龄" width="180" />
    <el-table-column prop="address" label="地址" />
  </el-table>



  <el-dialog
    v-model="centerDialogVisible"
    title="增加新信息"
    width="30%"
    center
  >
  <div class="center" > 名称:<el-input style="display: inline;margin-left:10px;" v-model="nameInput" placeholder="请输入名称" /></div>
  <div class="center" style="margin-top:10px;"> 年龄:<el-input style="display: inline;margin-left:10px;" v-model="ageInput" placeholder="请输出年龄" /></div>
  <div class="center" style="margin-top:10px;">地址:<el-input style="display: inline;margin-left:10px;" v-model="addressInput" placeholder="请输入地址" /></div>   
  

    <template #footer>
      <span class="dialog-footer">
        <el-button @click="cancel">取消</el-button>
        <el-button type="primary" @click="confirm">
          确认
        </el-button>
      </span>
    </template>
  </el-dialog>
</template>

<style scoped>
.center{
  text-align:center;
}
</style>
<script setup lang="ts">
import { reactive,ref } from 'vue';
// 名称 年龄 地址 对话框状态
const nameInput = ref('')
const ageInput = ref('')
const addressInput = ref('')
const centerDialogVisible = ref(false)
//表格数据
const tableData = reactive([
    {
    name: "网络语00000000",
    age: "11",
    address: "浙江",
  },
  {
    name: "网络语111111",
    age: "12",
    address: "河南",
  }])
  // 点击取消
  const cancel=()=>{
    centerDialogVisible.value=false;
    nameInput.value='';
    ageInput.value='';
    addressInput.value='';
  }
  // 点击确认
  const confirm=()=>{
    if(!nameInput.value||!ageInput.value||!addressInput.value){
      alert("请填写全部内容")
      return
    }
    tableData.push({name:nameInput.value,age:ageInput.value,address:addressInput.value})
    centerDialogVisible.value=false;
    nameInput.value='';
    ageInput.value='';
    addressInput.value='';
  }
</script>