<script setup>
import { ref } from "vue";

const tableData = [
    {
        date: '2016-05-03',
        name: 'Tom1',
        address: 'No. 189, Grove St, Los Angeles',
    },
    {
        date: '2016-05-02',
        name: 'Tom2',
        address: 'No. 189, Grove St, Los Angeles',
    },
    {
        date: '2016-05-04',
        name: 'Tom3',
        address: 'No. 189, Grove St, Los Angeles',
    },
    {
        date: '2016-05-01',
        name: 'Tom4',
        address: 'No. 189, Grove St, Los Angeles',
    },
]

// 分页条
const currentPage4 = ref(1); // 当前页面
const pageSize4 = ref(100); // 每页展示记录数
const total = ref(400); // 总记录数
const background = ref(true); // 是否显示背景色

const handleSizeChange = (val) => {
    console.log(`每页展示：${val} 条`);
}
const handleCurrentChange = (val) => {
    console.log(`当前页码是: ${val}`);
}

const dialogTableVisible = ref(false) // 对话框是否可见

// 表单组件相关
const user = ref({
    name: '',
    gender: '',
    birthday: ''
})

const onSubmit = () => {
    console.log(user.value)
}

</script>


<template>
    <!-- 按钮 -->
    <div class="mb-4">
        <el-button>Default</el-button>
        <el-button type="primary">Primary</el-button>
        <el-button type="success">Success</el-button>
        <el-button type="info">Info</el-button>
        <el-button type="warning">Warning</el-button>
        <el-button type="danger">Danger</el-button>
    </div>

    <div class="mb-4">
        <el-button plain>Plain</el-button>
        <el-button type="primary" plain>Primary</el-button>
        <el-button type="success" plain>Success</el-button>
        <el-button type="info" plain>Info</el-button>
        <el-button type="warning" plain>Warning</el-button>
        <el-button type="danger" plain>Danger</el-button>
    </div>

    <!-- 表格 -->
    <div class="mb-4">
        <el-table :data="tableData" border style="width: 100%">
            <el-table-column prop="date" label="生日" width="260" align="center" />
            <el-table-column prop="name" label="姓名" width="260" align="center" />
            <el-table-column prop="address" label="住址" align="center" />
        </el-table>
    </div>

    <!-- 分页条 -->
    <div class="mb-4">
        <el-pagination v-model:current-page="currentPage4" v-model:page-size="pageSize4"
            :page-sizes="[10, 20, 30, 40, 50, 75, 100]" :background="background"
            layout="total, sizes, prev, pager, next, jumper" :total="total" @size-change="handleSizeChange"
            @current-change="handleCurrentChange" />
    </div>

    <!-- 对话框 -->
    <div class="mb-4">
        <el-button plain @click="dialogTableVisible = true">打开Dialog对话框</el-button>

        <el-dialog v-model="dialogTableVisible" title="收货地址" width="800">
            <el-table :data="tableData">
                <el-table-column property="date" label="日期" width="150" />
                <el-table-column property="name" label="姓名" width="200" />
                <el-table-column property="address" label="地址" />
            </el-table>
        </el-dialog>



    </div>

    <!-- 表单组件 -->
    <div class="mb-4">
        <el-form :inline="true" :model="user" class="demo-form-inline">
            <el-form-item label="姓名">
                <el-input v-model="user.name" placeholder="请输入姓名" clearable />
            </el-form-item>
            <el-form-item label="性别">
                <el-select v-model="user.gender" placeholder="请输入性别" clearable>
                    <el-option label="男" value="1" />
                    <el-option label="女" value="2" />
                </el-select>
            </el-form-item>
            <el-form-item label="生日">
                <el-date-picker v-model="user.birthday" type="date" placeholder="请选择生日" value-format="YYYY-MM-DD"
                    clearable />
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="onSubmit">Query</el-button>
            </el-form-item>
        </el-form>
    </div>

    <!-- 布局组件 -->
    <div class="mb-4">
        <el-container>
            <el-header>Header</el-header>
            <el-container>
                <el-aside width="200px">Aside</el-aside>
                <el-container>
                    <el-main>Main</el-main>
                    <el-footer>Footer</el-footer>
                </el-container>
            </el-container>
        </el-container>
    </div>
</template>




<style scoped>
.mb-4 {
    margin-bottom: 10px;
}

.demo-form-inline .el-input {
    --el-input-width: 220px;
}

.demo-form-inline .el-select {
    --el-select-width: 220px;
}
</style>
