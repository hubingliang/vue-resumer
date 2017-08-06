<template>
  <div class="app" id="app" v-bind:class="{previewMode: previewMode}">
    <Topbar class="topbar" v-on:preview="preview"/>
    <main>
    <Editor v-bind:resume="resume" class="editor"/>
    <Preview v-bind:resume="resume" class="preview"v-on:exitpreview="exitpreview"/>
    </main>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'
export default {
  data(){
    return {
      previewMode : false,
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
        contacts:
          {qq:'',wechat:'',email:'',phone:''}
        
      },
    }
  },
  methods:{
    preview(){
      this.previewMode = true
    },
    exitpreview(){
      this.previewMode = false
    },
  },
  name: 'app',
  components: {
    Topbar,Editor,Preview
  },
}
</script>


