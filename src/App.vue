<template>
  <h2>福建方志方言词库</h2>
  <div class="wrapper input-warpper">
    <el-input v-model="input" placeholder="Please input" />
    <el-button @click="handleSearch">搜索</el-button>
  </div>
  <div class="wrapper operate-wrapper">
    <el-button @click="openModal">添加</el-button>
    <el-button @click="delMultiple">批量删除</el-button>
  </div>
  <Table :data="list" @edit="handleEdit" ref="tableRef" @delete="loadData"></Table>
  <Modal :data="modalData" v-model="visible" @update:visible="closeModal"></Modal>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { clone } from 'lodash-es'
import Table from './components/Table.vue'
import Modal from './components/Modal.vue'
import mock from './mock'

const input = ref('')
const tableRef = ref()
const list = ref([])
const visible = ref(false)
const modalData = ref({})

const openModal = () => {
  visible.value = true
}

const closeModal = () => {
  visible.value = false
  modalData.value = {}
}

const loadData = () => {
  // 请求表格接口
  // fetch('').then(res => {
  //   list.value = res.data
  // })
  list.value = mock.data
}

const handleEdit = (data) => {
  visible.value = true
  modalData.value = clone(data)
}

const delMultiple = () => {
  const ids = tableRef.value.getAllSelections().map(d => d.id)
  if (!ids.length) return
  // 请求批量删除接口
  // fetch('').then(res => {
  //   loadData()
  // })
}

// 搜索逻辑
const handleSearch = () => {
  // 请求表格接口，搜索参数是input
  // fetch('').then(res => {
  //   list.value = res.data
  // })
  list.value = mock.data
}

onMounted(() => {
  loadData()
})

</script>

<style lang="scss" scoped>
.wrapper {
  display: flex;
  align-items: center;
}

.input-warpper {
  margin-bottom: 30px;
}

.input-warpper,
.operate-wrapper {
  .el-button {
    margin-left: 4px;
  }
}

.operate-wrapper {
  margin-bottom: 10px;
}
</style>
