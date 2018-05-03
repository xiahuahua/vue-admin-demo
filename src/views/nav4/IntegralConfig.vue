<template>
    <div>
        <el-col>
            <h1>积分规则配置</h1>
        </el-col>
        <el-form>
            <el-form-item label="第1-2天：">
                <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10"
                                 label="描述文字"></el-input-number>
            </el-form-item>
            <el-form-item label="第3-4天：">
                <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10"
                                 label="描述文字"></el-input-number>
            </el-form-item>
            <el-form-item label="第5-6天：">
                <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10"
                                 label="描述文字"></el-input-number>
            </el-form-item>
            <el-form-item label="7天以上：">
                <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10"
                                 label="描述文字"></el-input-number>
            </el-form-item>
            <el-button type="primary">保存配置</el-button>
        </el-form>
    </div>
</template>

<script>
    export default {
        name: "integral-config",
        data() {
            return {
                num1: 1
            }
        },
        methods: {
            handleChange() {
                console.log('handleChange!');
            }
        }
    }
</script>

<style scoped>

</style>