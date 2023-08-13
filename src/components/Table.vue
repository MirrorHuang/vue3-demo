<template>
    <div class="table-container">
        <el-table :data="data" @selection-change="handleSelectionChange">
            <el-table-column type="selection" width="55" />
            <el-table-column property="words" label="词语" width="60" show-overflow-tooltip align="center" />
            <el-table-column property="pronunciation" label="注音" show-overflow-tooltip align="center" />
            <el-table-column property="meaning" label="释义" show-overflow-tooltip align="center" />
            <el-table-column property="genre" label="词类" show-overflow-tooltip align="center" />
            <el-table-column property="form" label="语类" show-overflow-tooltip align="center" />
            <el-table-column property="biaozhuncixing" label="标准词形" show-overflow-tooltip align="center" />
            <el-table-column property="zhuyin" label="标准注音" show-overflow-tooltip align="center" />
            <el-table-column property="biaozhuncilei" label="标准词类" show-overflow-tooltip align="center" />
            <el-table-column property="biaozhunyulei" label="标准语类" show-overflow-tooltip align="center" />
            <el-table-column property="fuzhu" label="附注" show-overflow-tooltip align="center" />
            <el-table-column property="area" label="分布地域" show-overflow-tooltip align="center" />
            <el-table-column property="date" label="通行时间" width="110" align="center" />
            <el-table-column label="操作" min-width="140" align="center">
                <template #default="scope">
                    <el-button size="small" @click="handleEdit(scope.row)">编辑</el-button>
                    <el-button size="small" type="danger" @click="handleDelete(scope.row)">删除</el-button>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>
  
<script setup>
import { ref } from 'vue'
defineProps({
    data: Array
})
const selections = ref([])

const emit = defineEmits(['edit', 'loadData'])

// 编辑逻辑
const handleEdit = (data) => {
    emit('edit', data)
}
// 删除逻辑
const handleDelete = (data) => {
    // 请求接口，删除数据
    // fetch('xxx').then(res => {
    // 删除成功后重新请求表格数据
    //      emit('loadData')
    // })
}

const handleSelectionChange = (val) => {
    selections.value = val
}

const getAllSelections = ()=> selections.value

defineExpose({
    getAllSelections
})

</script>
  
<style lang="scss" scoped>
.input-warpper {
    display: flex;
    align-items: center;

    .el-button {
        margin-left: 4px;
    }

}
</style>
  