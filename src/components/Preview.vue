<template>
    <div id="preview">
        <h1 class="name">{{resume.profile.name}}</h1>
        <p>{{resume.profile.city}} | {{resume.profile.birth}}</p>
        <hr>
        <h2>工作经历</h2>
        <section v-if="filter(resume.workExperience).length>0" class="workExperience">
            <ul>
                <li v-for="workExperience in filter(resume.workExperience)">
                    <h3>{{workExperience.conmpany}}</h3>
                    <p>{{workExperience.content}}</p>
                </li>
            </ul>
        </section>
        <hr>
        <h2>学习经历</h2>
        <section v-if="filter(resume.Learningexperience).length>0" class="Learningexperience">
            <ul>
                <li v-for="Learningexperience in filter(resume.Learningexperience)">
                    <div class="school">
                        <h3>{{Learningexperience.school}}</h3>
                        <span>{{Learningexperience.time}}</span>
                    </div>
                    <p>{{Learningexperience.degree}}</p>
                </li>
            </ul>
        </section>
        <hr>
        <h2>项目经历</h2>
        <section v-if="filter(resume.Projectexperience).length>0">
            <ul>
                <li v-for="Projectexperience in filter(resume.Projectexperience)">
                    <h3>{{Projectexperience.name}}</h3>
                    <p>{{Projectexperience.content}}</p>
                </li>
            </ul>
        </section>
        <hr>
        <h2>奖项</h2>
        <section v-if="filter(resume.Awards).length>0">
            <ul>
                <li v-for="Awards in filter(resume.Awards)">            
                    <p>{{Awards.name}}</p>
                </li>
            </ul>
        </section>
        <hr>
        <h2>联系方式</h2>
        <section class="contacts">
            <ul>
                <li>            
                   QQ：{{resume.contacts.qq}}
                </li>
                <li>            
                   微信：{{resume.contacts.wechat}}
                </li>
            </ul>
            <ul>
                <li>            
                   邮箱：{{resume.contacts.email}}
                </li>
                <li>            
                   电话：{{resume.contacts.phone}}
                </li>
            </ul>
        </section>
        <hr>
        <el-button v-on:click="exitpreview" class="exitpreview"type="primary">退出预览</el-button>
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