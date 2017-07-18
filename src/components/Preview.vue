<template>
    <div id="preview">
        <h1>{{resume.profile.name}}</h1>
        <hr>
        <p>{{resume.profile.city}} | {{resume.profile.birth}}</p>
    </div>
</template>


<script>
export default {
  props:['resume']
}
</script>

<style>
#preview {
}
</style>
