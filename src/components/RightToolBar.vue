<!--
 * @Author: yaolunmao
-->
<template>
<div class="rightNav">
<a-tabs type="card"  class="components-layout-right">
    <a-tab-pane key="1" tab="外观">
      <a-form layout="horizontal"  :label-col="{ span: 6 }" :wrapper-col="{ span: 10 }" labelAlign="left">
        <a-form-item label="id">
          <p>{{svgInfo.id}}</p>
        </a-form-item>
        <a-form-item label="类型">
          <p>{{selectSvgInfo.typeName}}</p>
        </a-form-item>
        <a-form-item label="名称">
          <a-input v-model:value="selectSvgInfo.title" placeholder="请输入组件名称" />
        </a-form-item>
        <a-form-item label="X轴坐标">
          <a-input-number v-model:value="selectSvgInfo.svgPositionX" :min="0" :max="1920"/>
        </a-form-item>
        <a-form-item label="Y轴坐标">
          <a-input-number v-model:value="selectSvgInfo.svgPositionY" :min="0" :max="1080"/>
        </a-form-item>
        <a-form-item label="颜色">
          <input type="color" v-model="selectSvgInfo.svgColor">
        </a-form-item>
        <a-form-item label="大小">
          <a-input-number v-model:value="selectSvgInfo.size" :min="1" :max="3000" step="0.1"/>
        </a-form-item>
        <a-form-item label="旋转">
          <a-input-number v-model:value="selectSvgInfo.angle" :min="0" :max="360"/>
        </a-form-item>
        <a-form-item>
          <a-button type="primary" class="btn-sure">
            确定
          </a-button>
        </a-form-item>
      </a-form>
    </a-tab-pane>
    <a-tab-pane key="2" tab="数据">
      <div class="bg-code">{{selectSvgInfo}}</div>
    </a-tab-pane>
  </a-tabs>
</div>
</template>
<script>
export default {
  props: ['svgInfo'],
  computed:{
    selectSvgInfo(){
      return this.svgInfo;
    }
  },
  watch:{
    'selectSvgInfo.tableRowCount':function(newVal){
      this.$emit('setTableAttr', this.selectSvgInfo.id,newVal,this.selectSvgInfo.tableColCount)
    },
    'selectSvgInfo.tableColCount':function(newVal){
      this.$emit('setTableAttr', this.selectSvgInfo.id,this.selectSvgInfo.tableRowCount,newVal)
    }
  }
};
</script>
<style scoped lang="less">
.components-layout-right{
  .ant-tabs-bar{
    margin-bottom: 0 !important;
  }
  .ant-form-item-label{
    width: 100px !important;
    flex-shrink: 0;
  }
  .ant-input-number,input{
    width: 160px;
    border-radius: 4px;
    border-color: #ddd;
  }
  .ant-form-item-control{
    line-height: 24px !important;

    p{
      margin-bottom: 0 !important;
    }

    
  }

  .ant-form-item{
    display: flex;
    align-items: center;
    flex-flow: nowrap;
    position: relative;
    margin-bottom: 0;
    padding: 8px 0;

    &:after{
      content:"";
      position: absolute;
      bottom: 0;
      left: 15px;
      right: 15px;
      bottom: 0;
      height: 1px;
    }

    &:last-child::after{
      content:unset
    }
  }
}
.btn-sure{
  width: 260px;
  margin: 20px;
}
.bg-code{
  background: #444;
  color: #fff;
  width: calc(100% - 20px);
  margin: 20px 10px;
  border-radius: 4px;
  padding: 10px;
}
.rightNav {
  right: 0;
  top: 0;
  bottom: 0;
  min-width: unset !important;
  max-width: unset !important;
  width: 300px !important;
  z-index: 1;
  overflow: auto;
  padding:10px 20px;
}
</style>
