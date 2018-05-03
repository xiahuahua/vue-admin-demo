<template>
    <div>
        <el-col>
            <h1>引导页配置</h1>
        </el-col>
        <el-form>
            <el-upload
                    action="https://jsonplaceholder.typicode.com/posts/"
                    list-type="picture-card"
                    :on-preview="handlePictureCardPreview1"
                    :on-remove="handleRemove1"
                    :file-list="fileList1">
                <i class="el-icon-plus"></i>
            </el-upload>
            <el-dialog :visible.sync="dialogVisible1">
                <img width="100%" :src="dialogImageUrl1" alt="">
            </el-dialog>
        </el-form>

        <div class="xline"></div>

        <el-col>
            <h1>宣传页配置
            <el-switch
                    style="display: block"
                    v-model="GuidePageConfig"
                    active-color="#13ce66"
                    inactive-color="#ff4949"
                    active-text="打开宣传页"
                    inactive-text="关闭宣传页">
            </el-switch>
            </h1>
        </el-col>
        <el-col>

        </el-col>
        <el-form>
            <el-upload
                    action="https://jsonplaceholder.typicode.com/posts/"
                    list-type="picture-card"
                    :on-preview="handlePictureCardPreview"
                    :on-remove="handleRemove"
                    :file-list="fileList2">
                <i class="el-icon-plus"></i>
            </el-upload>
            <el-dialog :visible.sync="dialogVisible">
                <img width="100%" :src="dialogImageUrl" alt="">
            </el-dialog>
        </el-form>

    </div>
</template>

<script>
    export default {
        name: "guide-page-config",
        data() {
            return {
                imageUrl: '',
                dialogImageUrl1: '',
                dialogVisible1: false,
                GuidePageConfig1: true,
                fileList1: [
                    {name: 'xc1.jpg', url: 'http://m.age06.com/abc/guideImg/xc1.jpg'},
                ],

                dialogImageUrl: '',
                dialogVisible: false,
                GuidePageConfig: true,
                fileList2: [
                    {name: 'xc1.jpg', url: 'http://m.age06.com/abc/guideImg/xc1.jpg'},
                    {name: 'xc2.jpg', url: 'http://m.age06.com/abc/guideImg/xc2.jpg'},
                    {name: 'xc2.jpg', url: 'http://m.age06.com/abc/guideImg/xc3.jpg'}
                ]
            };
        },
        methods: {
            handleRemove1(file, fileList) {
                console.log(file, fileList);
            },
            handlePictureCardPreview1(file) {
                this.dialogImageUrl1 = file.url;
                this.dialogVisible1 = true;
            },
            handleRemove(file, fileList) {
                console.log(file, fileList);
            },
            handlePictureCardPreview(file) {
                this.dialogImageUrl = file.url;
                this.dialogVisible = true;
            }
        }
    }
</script>

<style lang="scss">
    .avatar-uploader .el-upload {
        border: 1px dashed #d9d9d9;
        border-radius: 6px;
        cursor: pointer;
        position: relative;
        overflow: hidden;
    }

    .avatar-uploader .el-upload:hover {
        border-color: #409EFF;
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
    .xline{border-bottom:solid 1px #dfe9ee; height:5px;}
</style>