<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
    <Editor v-bind:resume="resume" class="editor"/>
    <Preview v-bind:resume="resume" class="preview"/>
    </main>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'
export default {
  data(){
    return {
      resume:{
          profile:{
          name:　'',
          city:'',
          birth: '',
        },
        workExperience:[
          {conmpany:'',content: ''}
        ],
        Learningexperience:[
          {school:'',time: '',degree: ''}
        ],
        Projectexperience:[
          {name:'',content: ''}
        ],
        Awards:[
          {name:''}
        ],
        contacts:[
          {qq:'',wechat:'',email:'',phone:''}
        ]
      }
    }
  },
  name: 'app',
  components: {
    Topbar,Editor,Preview
  }
}
</script>


