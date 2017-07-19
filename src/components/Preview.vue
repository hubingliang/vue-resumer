<template>
    <div id="preview">
        <el-upload
        class="avatar-uploader"
        action="https://jsonplaceholder.typicode.com/posts/"
        :show-file-list="false"
        :on-success="handleAvatarSuccess"
        :before-upload="beforeAvatarUpload">
            <img v-if="imageUrl" :src="imageUrl" class="avatar">
            <i v-else class="el-icon-plus avatar-uploader-icon"></i>
        </el-upload>
        <h1 class="name">{{resume.profile.name}}</h1>
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
        <section>
            <h2>联系方式</h2>
            <ul>
                <li>            
                   {{resume.contacts.qq}}
                </li>
                <li>            
                   {{resume.contacts.wechat}}
                </li>
                <li>            
                   {{resume.contacts.email}}
                </li>
                <li>            
                   {{resume.contacts.phone}}
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
        <el-button v-on:click="exitpreview" class="exitpreview"type="primary">退出预览</el-button>
    </div>
</template>


<script>
    export default {
        props: ['resume'],
        data() {
            return {
                imageUrl: ''
            };
        },
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
            },
            handleAvatarSuccess(res, file) {
                this.imageUrl = URL.createObjectURL(file.raw);
            },
            beforeAvatarUpload(file) {
                const isJPG = file.type === 'image/jpeg';
                const isLt2M = file.size / 1024 / 1024 < 2;

                if (!isJPG) {
                this.$message.error('上传头像图片只能是 JPG 格式!');
                }
                if (!isLt2M) {
                this.$message.error('上传头像图片大小不能超过 2MB!');
                }
                return isJPG && isLt2M;
            }
        },
        
    }
</script>

<style>
  .avatar-uploader .el-upload {
    border: 1px dashed #d9d9d9;
    border-radius: 6px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }
  .avatar-uploader .el-upload:hover {
    border-color: #20a0ff;
  }
  .avatar-uploader-icon {
    font-size: 28px;
    color: #8c939d;
    width: 178px;
    height: 178px;
    line-height: 178px;
    text-align: center;
  }
  .avatar {
    width: 178px;
    height: 178px;
    display: block;
  }
</style>