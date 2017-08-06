<template>
    <div id="topbar">
      <div class="logo">
          Vue Resumer
      </div>
      <div class="actions">
        <el-button v-on:click="preview" class="preview">预览</el-button>
      </div>
    </div>
</template>



<style>
#topbar {
  color: black;
  min-height: 60px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px;
  font-size: 20px;
}
</style>

<script>
  export default {
    methods:{
      preview(){
        this.$emit('preview') 
      },
    }
  }
</script>

