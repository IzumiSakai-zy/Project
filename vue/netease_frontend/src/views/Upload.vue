<template>
  <div class="upload">
    <!-- <el-upload
      class="upload-demo"
      accept="*/*"
      ref="upload"
      action="/api/song/upload"
      :on-preview="handlePreview"
      :on-remove="handleRemove"
      :file-list="fileList"
      :auto-upload="false"
    >
      <el-button slot="trigger" size="small" type="primary">选取歌曲</el-button>
      <el-button
        style="margin-left: 10px"
        size="small"
        type="success"
        @click="submitUpload"
        >上传到我的云盘</el-button
      >
      <div slot="tip" class="el-upload__tip">
        只能上传形如 'singer - songname.mp3' 的音频文件
      </div>
    </el-upload>
    <br />
    <el-upload
      class="upload-demo"
      action="/api/song/upload"
    >
    <el-button size="small" type="primary">点击上传</el-button>
    </el-upload> -->
    <el-upload
            class="upload-demo"
            action="/api/song/upload"
            accept="*/*"
            ref="upload"
            :on-preview="handlePreview"
            :on-remove="handleRemove"
            :before-remove="beforeRemove"
          >
            <el-button
              :span="3"
              size="small"
              type="info"
              class="el-icon-plus bg"
              round
              >上传音乐</el-button
            >
          </el-upload>
  </div>
</template>
<style scoped>
::v-deep .el-upload-list__item-name{
  display: none ! important;
}
::v-deep .el-icon-upload-success{
  display: none ! important;
}
::v-deep .el-icon-circle-check{
  display: none ! important;
}
::v-deep .el-upload .el-upload--text{
  display: none ! important;
}
</style>
<script>
export default {
  name: "Upload",
  data() {
    return {
      headers: {
        "Content-Type": "multipart/form-data",
        accept: "*/*",
        "Accept-Encoding": "gzip, deflate, br",
      },
    };
  },
  methods: {
    submitUpload() {
      this.$refs.upload.submit();
    },
    handleRemove(file, fileList) {
      console.log(file, fileList);
    },
    handlePreview(file) {
      console.log(file);
    },
  },
};
</script>
