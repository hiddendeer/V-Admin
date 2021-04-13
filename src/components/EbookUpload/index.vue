<template>
  <div class="upload-container">
    <el-upload
      drag
      :action="action"
      :on-error="onError"
      :headers="headers"
      :multiple="false"
      :limit="1"
      :before-upload="beforeUpload"
      :on-success="onSuccess"
      :on-remove="onRemove"
      :file-list="fileList"
      :on-exceed="onExceed"
      :disabled="disabled"
      show-file-list
      accept="application/epub+zip+mobi"
      class="image-upload"
    >
      <i class="el-icon-upload"></i>
      <div class="el-upload__text" v-if="fileList.length === 0">请将电子书拖入或<em>点击上传</em></div>
      <div class="el-upload__text" v-else>图书已上传</div>
    </el-upload>
  </div>
</template>

<script>
export default {
  props: {
    fileList: {
      type: Array,
      default() {
        return [];
      },
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      action: `${process.env.VUE_APP_BASE_API}book/upload`,
    };
  },

  computed: {
    headers() {
      return {
        Authorization: `Bearer token`,
      };
    },
  },
  methods: {
    beforeUpload(file) {
      this.$emit("beforeUpload", file);
    },
    onSuccess() {},
    onError(err, file) {
      console.log(err);
      console.log(file);
    },
    onRemove() {},
    onExceed() {
      this.$message({
        message: "每次只能上传一本电子书",
        type: "warning",
      });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>