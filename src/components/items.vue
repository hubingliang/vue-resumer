<template>
    <div>
        <h2>{{title}}</h2>
        <el-form :label-position="labelPosition" label-width="80px" >
            <div v-for="(work,index) in items" v-bind:key="'work'" class="form">
                <el-form-item  v-for="key in keys" v-bind:key="key" v-bind:label="labels[key] || key">
                    <el-input v-model="work[key]"></el-input>
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
    props:['items','labels','title',],
    computed:{
        keys(){
            return Object.keys(this.items[0])
        }
    },
    data(){
        return {
            labelPosition: 'top',
        }
    },
    methods:{
        addworkExperience(){
            const empty = {}
            this.keys.map((key)=>{
                empty[key] = ''
            })
            this.items.push(empty)
        },
        removeworkExperience(index){
            this.items.splice(index,1)
        }
    }
}
</script>
