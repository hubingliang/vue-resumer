<template>
    <div id="topbar">
      <div class="logo">
          Vue-resumer
      </div>
      <div class="actions">
        <el-button>默认按钮</el-button>
        <el-button type="primary">主要按钮</el-button>
      </div>
    </div>
</template>



<style>
#topbar {
  color: red;
  border: 1px solid red;
  min-height: 60px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
}
</style>
