<template>
  <div class="main-left">
    <el-form>
      <div class="formleft">
        <el-select v-model="translateType" placeholder="请选择" size="small" class="selectOption">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-button type="primary" size="small" @click="onSubmit()" class="submitOption">翻译</el-button>
      </div>
      <div class="main-left-text">
        <el-input
          type="textarea"
          :autosize="{ minRows: 7}"
          placeholder="请输入需要翻译的内容"
          v-model="userText" style="font-size: 20px">
        </el-input>
      </div>
    </el-form>
  </div>
</template>
<style lang="scss">
  .main-left {
    padding-top: 30px;
    .formleft {
      .selectOption {
        float: left;
        margin-left: 40px;
      }
      .submitOption {
        float: right;
        width: 150px;
        margin-right: 40px;
      }
    }
    .main-left-text{
      clear: both;
      padding-top: 10px;
    }
  }

</style>
<script>
  export default {
    name: 'translateform',
    data: function () {
      return {
        options: [
          {
            value: 'en',
            label: '英语'
          }, {
            value: 'zh',
            label: '中文'
          }, {
            value: 'ko',
            label: '韩语'
          }, {
            value: 'ja',
            label: '日语'
          }, {
            value: 'fr',
            label: '法语'
          }, {
            value: 'de',
            label: '德语'
          }, {
            value: 'pt',
            label: '葡萄牙语'
          }],
        translateType: 'en',
        userText: '',
      }
    },
    methods: {
      onSubmit() {
        if (this.userText == '') {
          this.$message.error('请输入需要翻译的内容！');
        } else {
//            注册事件，传递事件名，参数
          this.$emit('formSub', this.userText, this.translateType);
        }
      }
    }
  }
</script>
