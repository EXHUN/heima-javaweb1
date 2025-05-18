<script setup>
import { ref } from "vue";

// 表单组件相关
const emp = ref({ name: '', gender: '', job: '' })

// 查询
const search = () => {

}

// 清空
const clear = () => {

}

// 表格相关
const empList = [
    {
        "id": 1,
        "name": "谢逊",
        "image": "https://web-framework.oss-cn-hangzhou.aliyuncs.com/2023/4.jpg",
        "gender": 1,
        "job": "1",
        "entrydate": "2023-06-09",
        "updatetime": "2025-04-15T23:42:24"
    }
]


</script>

<template>
    <div id="container">
        <!-- 搜索表单 -->
        <el-form :inline="true" :model="emp" class="demo-form-inline">
            <el-form-item label="姓名">
                <el-input v-model="emp.name" placeholder="请输入姓名" clearable />
            </el-form-item>
            <el-form-item label="性别">
                <el-select v-model="emp.gender" placeholder="请选择" clearable>
                    <el-option label="男" value="1" />
                    <el-option label="女" value="2" />
                </el-select>
            </el-form-item>
            <el-form-item label="职位">
                <el-select v-model="emp.job" placeholder="请选择" clearable>
                    <el-option label="班主任" value="1" />
                    <el-option label="讲师" value="2" />
                    <el-option label="学工主管" value="3" />
                    <el-option label="教研主管" value="4" />
                    <el-option label="咨询师" value="5" />
                </el-select>
            </el-form-item>

            <el-form-item>
                <el-button type="primary" @click="search">查询</el-button>
                <el-button type="info" @click="clear">清空</el-button>
            </el-form-item>

        </el-form>

        <!-- 表格 -->
        <el-table :data="empList" border style="width: 100%">
            <el-table-column prop="id" label="ID" width="100" align="center" />
            <el-table-column prop="name" label="姓名" width="120" align="center" />
            <el-table-column prop="image" label="头像" width="180" align="center" />
            <el-table-column prop="gender" label="性别" width="180" align="center" />
            <el-table-column prop="job" label="职位" width="180" align="center" />
            <el-table-column prop="entrydate" label="入职日期" width="180" align="center" />
            <el-table-column prop="updatetime" label="更新时间" align="center" />
        </el-table>
    </div>
</template>

<style scoped>
    #container {
        width: 70%;
        margin-left: 15%;
        margin-right: 15%;
    }
</style>
