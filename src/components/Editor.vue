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
          <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active:currentTab === i}">
            Tab{{i+1}}
          </li>
        </ol>
      </div>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        currentTab  : 0,
        icons: ['shenfenzheng','gongzuo','shu','xiangmu','jiangbei','dianhua'],

      }
    }
  }
</script>

<style>
#editor {
  fill: white;
}
</style>
