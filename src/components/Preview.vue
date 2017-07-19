<template>
    <div id="preview">
        <h1>{{resume.profile.name}}</h1>
        <hr>
        <p>{{resume.profile.city}} | {{resume.profile.birth}}</p>
        <hr>
        <section v-if="filter(resume.Projectexperience).length>0">
            <h2>项目经历</h2>
            <ul>
                <li v-for="Projectexperience in filter(resume.Projectexperience)">
                    {{Projectexperience.name}}
                    {{Projectexperience.content}}
                </li>
            </ul>
        </section>
        <section v-if="filter(resume.Learningexperience).length>0">
            <h2>学习经历</h2>
            <ul>
                <li v-for="Learningexperience in filter(resume.Learningexperience)">
                    
                    {{Learningexperience.school}}
                    {{Learningexperience.time}}
                    {{Learningexperience.degree}}
                </li>
            </ul>
        </section>
                <section v-if="filter(resume.workExperience).length>0">
            <h2>工作经历</h2>
            <ul>
                <li v-for="workExperience in filter(resume.workExperience)">
                    
                    {{workExperience.conmpany}}
                    {{workExperience.content}}
                </li>
            </ul>
        </section>
                <section v-if="filter(resume.Awards).length>0">
            <h2>奖项</h2>
            <ul>
                <li v-for="Awards in filter(resume.Awards)">            
                    {{Awards.name}}
                </li>
            </ul>
        </section>
        <el-button v-on:click="exitpreview" class="exitpreview">退出预览</el-button>
    </div>
</template>


<script>
    export default {
        props: ['resume'],
        methods: {
            filter(array) {
                return array.filter(item => !this.isempty(item))
            },
            isempty(object) {
                let empty = true
                for (let key in object) {
                    if (object[key]) {
                        empty = false
                        break
                    }
                }
                return empty
            },
            exitpreview(){
                this.$emit('exitpreview') 
            }
        },
        
    }
</script>

<style>
    #preview {}
</style>