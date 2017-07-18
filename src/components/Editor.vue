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
              <PersonalInformation v-bind:profile="profile"/>
            </li>
            <li  v-bind:class="{active:currentTab === 1}">
              <workExperience v-bind:profile="workExperience"/>
            </li>
            <li v-bind:class="{active:currentTab === 2}"></li>
            <li v-bind:class="{active:currentTab === 3}"></li>
            <li v-bind:class="{active:currentTab === 4}"></li>
            <li v-bind:class="{active:currentTab === 5}"></li>
        </ol>
      </div>
  </div>
</template>

<script>
  import PersonalInformation from './PersonalInformation'
  import workExperience from './workExperience'
  export default {
    components:{PersonalInformation,workExperience},
    data(){
      return {
        currentTab  : 0,
        icons: ['shenfenzheng','gongzuo','shu','xiangmu','jiangbei','dianhua'],
        labelPosition: 'top',
        profile:{
          name:　'',
          city:'',
          birth: '',
        },
        workExperience:[
          {conmpany:'',content: ''}
        ]
      }
    }
  }
</script>

<style>
#editor {
  fill: white;
}
</style>
