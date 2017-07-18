<template>
  <div id="editor">
    <nav>
        <ol>
          <li v-for="i in [0,1,2,3,4,5]" 
          v-bind:class="{active:currentTab === i}"  v-on:click="currentTab = i">
              <svg class="icon" aria-hidden="true">
                  <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
              </svg>
          </li>
        </ol>
    </nav>
      <div class="panes">
        <ol>
            <li v-bind:class="{active:currentTab === 0}">
              <PersonalInformation v-bind:profile="resume.profile"/>
            </li>
            <li  v-bind:class="{active:currentTab === 1}">
              <workExperience v-bind:items="resume.workExperience" v-bind:labels="{conmpany:'公司',content:'工作内容'}" v-bind:title="'工作经历'"/>
            </li>
            <li v-bind:class="{active:currentTab === 2}">
              <workExperience v-bind:items="resume.Learningexperience" v-bind:labels="{school:'学校',time:'时间',degree:'学位'}" v-bind:title="'学习经历'"/>
            </li>
            <li v-bind:class="{active:currentTab === 3}">
              <workExperience v-bind:items="resume.Projectexperience" v-bind:labels="{name:'项目',content:'具体内容'}" v-bind:title="'项目经历'"/>
            </li>
            <li v-bind:class="{active:currentTab === 4}">
              <workExperience v-bind:items="resume.Awards" v-bind:labels="{name:'获奖情况'}" v-bind:title="'获奖情况'"/>
            </li>
            <li v-bind:class="{active:currentTab === 5}">
              <h2>联系方式</h2>
              <el-form  :label-position="labelPosition" label-width="80px" >
                  <div class="form">
                      <el-form-item label="QQ">
                      <el-input v-model="resume.contacts.qq"></el-input>
                      </el-form-item>
                      <el-form-item label="微信">
                      <el-input v-model="resume.contacts.wechat"></el-input>
                      </el-form-item>
                      <el-form-item label="邮箱">
                      <el-input v-model="resume.contacts.email"></el-input>
                      </el-form-item>
                      <el-form-item label="手机">
                      <el-input v-model="resume.contacts.phone"></el-input>
                      </el-form-item>
                  </div>
              </el-form>
            </li>
        </ol>
      </div>
  </div>
</template>

<script>
  import PersonalInformation from './PersonalInformation'
  import workExperience from './items'
  export default {
    props:['resume'],
    components:{PersonalInformation,workExperience},
    data(){
      return {
        currentTab  : 0,
        icons: ['shenfenzheng','gongzuo','shu','xiangmu','jiangbei','dianhua'],
        labelPosition: 'top',
      }
    }
  }
</script>

<style>
#editor {
  fill: white;
}
</style>
