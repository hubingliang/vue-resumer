<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
    <Editor class="editor"/>
    <Preview class="preview"/>
    </main>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'
export default {
  name: 'app',
  components: {
    Topbar,Editor,Preview
  }
}
</script>


