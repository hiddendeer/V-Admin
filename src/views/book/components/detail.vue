<template>
  <el-form ref="postForm" :model="postForm">
    <sticky :class-name="'sub-navbar ' + postForm.status">
      <el-button v-if="!isEdit">显示帮助</el-button>
      <el-button
        v-loading="loading"
        type="success"
        style="margin-left: 10px"
        @click="submitForm"
        >{{ isEdit ? "编辑电子书" : "新增电子书" }}</el-button
      >
    </sticky>
    <div class="detail-container">
      <router-link :to="{name: 'bookCreate'}"><span>在线更新</span></router-link>
      <el-row>
        <Warning /> 
        <!-- 表单控件的具体样式 -->
        <el-col :span="24">
          <ebook-upload></ebook-upload>
        </el-col>
        <el-col :span="24"></el-col>
      </el-row>
    </div>
  </el-form>
</template>
<script>
/* eslint-disable */
import Sticky from "../../../components/Sticky";
import EbookUpload from "@/components/EbookUpload";
import Warning from "./Warning";

export default {
  components: { Sticky, Warning, EbookUpload },
  props: {
    isEdit: Boolean,
  },
  data() {
    return {
      loading: false,
      postForm: {
        status: "subtitle",
      },
    };
  },

  mounted() {


  },
  methods: {
    onSubmit() {
      console.log(11);
    },
    submitForm() {
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 1000);
    },
  },
};
</script>

<style lang="scss" scoped>
  .detail-container {
    padding: 40px 50px 20px;
  }
  
</style>