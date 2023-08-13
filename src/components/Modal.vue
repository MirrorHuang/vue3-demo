<template>
    <el-dialog v-model="diaglogVisible" :title="data ? '编辑' : '新增'">
        <div class="body">
            <el-form :model="data" label-width="80px">
                <el-row>
                    <el-col :span="12">
                        <el-form-item label="词语">
                            <el-input v-model="data.words" />
                        </el-form-item>
                    </el-col>
                    <el-col :span="12">
                        <el-form-item label="注音">
                            <el-input v-model="data.pronunciation" />
                        </el-form-item>
                    </el-col>
                </el-row>
                <el-row>
                    <el-col :span="12">
                        <el-form-item label="释义">
                            <el-input v-model="data.meaning" />
                        </el-form-item>
                    </el-col>
                    <el-col :span="12">
                        <el-form-item label="语类">
                            <el-select v-model="data.form">
                                <el-option label="天文地理" value="tianwendili" />
                                <el-option label="天文地理2" value="tianwendili2" />
                            </el-select>
                        </el-form-item>
                    </el-col>
                </el-row>
                <el-row>
                    <el-col :span="12">
                        <el-form-item label="词类">
                            <el-input v-model="data.genre" />
                        </el-form-item>
                    </el-col>
                    <el-col :span="12">
                        <el-form-item label="标准词形">
                            <el-input v-model="data.biaozhuncixing" />
                        </el-form-item>
                    </el-col>

                </el-row>
                <el-row>
                    <el-col :span="12">
                        <el-form-item label="标准语类">
                            <el-input v-model="data.biaozhunyulei" />
                        </el-form-item>
                    </el-col>
                    <el-col :span="12">
                        <el-form-item label="标准语类">
                            <el-input v-model="data.biaozhuncilei" />
                        </el-form-item>
                    </el-col>
                </el-row>
                <el-row>
                    <el-col :span="12">
                        <el-form-item label="标准注音">
                            <el-input v-model="data.zhuyin" />
                        </el-form-item>
                    </el-col>
                    <el-col :span="12">
                        <el-form-item label="通行时间">
                            <el-input v-model="data.date" />
                        </el-form-item>
                    </el-col>

                </el-row>

                <el-row>
                    <el-col :span="12">
                        <el-form-item label="分布地域">
                            <el-input v-model="data.area" />
                        </el-form-item>
                    </el-col>
                    <el-col :span="12">
                        <el-form-item label="附注">
                            <el-input v-model="data.fuzhu" />
                        </el-form-item>
                    </el-col>
                </el-row>
            </el-form>
        </div>

        <template #footer>
            <span class="dialog-footer">
                <el-button @click="close">取消</el-button>
                <el-button type="primary" @click="handleConfirm">
                    确定
                </el-button>
            </span>
        </template>
    </el-dialog>
</template>
  
<script setup>
import { computed } from 'vue'
const props = defineProps({
    visible: Boolean,
    data: Object
})

const emit = defineEmits(['update:visible'])

const diaglogVisible = computed({
    get() {
        return props.visible
    },
    set(value) {
        emit('update:visible', value)
    }
})

const close = () => {
    emit('update:visible')
}

const handleConfirm = () => {
    if (props.data.id) {
        // 编辑
        // 请求编辑接口，参数是
        // return fetch('xxxx', {
        //     method: 'post',
        //     body: JSON.stringify(props.data)
        // }).then(res => {
        // close()
        // })
    }
    // // 请求新增接口，参数是
    // fetch('xxxx', {
    //     method: 'post',
    //     body: JSON.stringify(props.data)
    // }).then(res => {
    // close()
    // })

}
</script>
<style lang="scss" scoped>
.body {
    .row {
        display: flex;
        align-items: center;
    }
}
</style>