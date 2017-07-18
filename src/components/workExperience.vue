<template>
    <div>
        <h2>工作经历</h2>
        <el-form :label-position="labelPosition" label-width="80px" >
            <div v-for="(work,index) in workExperience" class="form">
                <el-form-item label="公司">
                    <el-input v-model="work.name"></el-input>
                </el-form-item>
                <el-form-item label="工作经历">
                    <el-input v-model="work.city"></el-input>
                </el-form-item>
                <div class="action">
                    <el-button type="primary" v-on:click="addworkExperience">增加</el-button>
                    <i class="el-icon-delete" v-on:click="removeworkExperience(index)"></i>
                </div>
            </div>
        </el-form>
    </div>
</template>

<script>
export default {
    data(){
        return {
            labelPosition: 'top',
            workExperience:[
            {conmpany:'',content: ''}
            ]
        }
    },
    methods:{
        addworkExperience(){
            this.workExperience.push({
                conmpany: '',
                content:''
            })
        },
        removeworkExperience(index){
            this.workExperience.splice(index,1)
        }
    }
}
</script>
