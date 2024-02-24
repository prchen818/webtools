<script setup lang="ts">
import { ref } from 'vue';
import { Plus, Switch } from '@element-plus/icons-vue'
import { ElMessage } from 'element-plus';

const imgUrl = ref("")
const result = ref("")
const handlePreview = (file: any) => {
  const isJPG = file.raw.type === 'image/jpeg'
  if (!isJPG) {
    ElMessage.error("图片格式错误")
    return
  }
  imgUrl.value = URL.createObjectURL(file.raw)
}
</script>

<template>
  <div class="main">
    <ElSpace wrap :size="50">
      <div class="block">
        <ElSpace wrap direction="vertical">
          <ElImage class="qrimg" v-if="imgUrl" :src="imgUrl" fit="contain"></ElImage>
          <ElUpload v-else class="img-box" :auto-upload="false" :on-change="handlePreview">
            <ElIcon class="upload-icon">
              <Plus />
            </ElIcon>
          </ElUpload>
          <ElButton>上传</ElButton>
        </ElSpace>
      </div>
      <ElIcon class="switch-icon">
        <Switch />
      </ElIcon>
      <div class="text-box">
        <ElText v-if="!result" type="info" size="large">上传二维码以解析内容</ElText>
      </div>
    </ElSpace>
  </div>
</template>
<style scoped>
.main {
  height: 100%;
  width: 100%;
  padding: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.block {
  height: 200px;
  width: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.qrimg,
.img-box {
  height: 200px;
  width: 200px;
  border: 1px dashed var(--el-border-color);
  border-radius: 6px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.img-box {
  cursor: pointer;
}

.upload-icon {
  font-size: 28px;
  color: #8c939d;
  text-align: center;

}

.switch-icon {
  font-size: 48px;
  color: #8c939d;
  text-align: center;
}
</style>