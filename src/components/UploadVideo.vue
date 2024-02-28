<template>
  <el-row>
    <el-col :span="16">
      <video v-if="processedUrl" :src="processedUrl" width="95%" controls></video>
      <div v-else v-for="(file, index) in fileList" :key="index">
        <video controls width="50%" :src="createObjectURLForFile(file.raw)"></video>
      </div>
    </el-col>

    <el-col :span="8">
      <el-upload v-model:file-list="fileList" ref="uploadRef" drag :action="baseUrl" multiple :auto-upload="false"
        accept="video/*" @success="handleSuccess" @preview="handlePreview">
        <el-icon class="el-icon--upload"><upload-filled /></el-icon>
        <div class="el-upload__text">
          Drop file here or <em>click to upload</em>
        </div>
        <template #tip>
          <div class="el-upload__tip">
            video files
          </div>
        </template>
      </el-upload>
      <el-divider />
      <el-button type="success" size="large" class="btn-pos" @click="uploadRef.submit()">提交</el-button>
      <br>
      <br>
      <br>
      <br>
      人数：{{person_num}}
    </el-col>
  </el-row>
</template>


<script setup>
import { ref } from 'vue'
import { UploadFilled } from '@element-plus/icons-vue'

const baseUrl = "http://127.0.0.1:5000"   //后端地址
const uploadRef = ref()
var processedUrl = ref("")
var person_num = ref(0)
const fileList = ref([])

const handleSuccess = (response) => {
  processedUrl.value = baseUrl + response.url
  person_num.value = response.num
}
const handlePreview = (uploadFile) => {  //点击文件恢复为预览界面
  processedUrl.value = ""
}
const createObjectURLForFile = (file) => {  //原生createObjectURLForFile好像不能直接读取file.raw
  if (file) {
    return window.URL.createObjectURL(file);
  }
  return "";
}
</script>
   
   
<style scoped>
.btn-pos {
  float: right;
}
</style>
   