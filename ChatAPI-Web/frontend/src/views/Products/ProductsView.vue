<template>
    <view-box>
        <div class="main-box">
            <div class="common-layout">
                <el-container>

                    <el-aside width="200px">
                        <el-radio-group v-model="isCollapse" style="margin-bottom: 20px">
                            <el-radio-button :label="false">expand</el-radio-button>
                            <el-radio-button :label="true">collapse</el-radio-button>
                        </el-radio-group>
                        <el-menu default-active="1" class="el-menu-vertical-demo" :collapse="isCollapse" @open="handleOpen"
                            @close="handleClose" @select="handleSelect">
                            <!-- 首页 -->
                            <el-menu-item index="1">
                                <el-icon>
                                    <Grid />
                                </el-icon>
                                <template #title>首页</template>
                            </el-menu-item>
                            <!-- 设备报修 -->
                            <el-menu-item index="2" @click="openDialog">
                                <el-icon>
                                    <Help />
                                </el-icon>
                                <template #title>设备报修</template>
                            </el-menu-item>
                            <!-- 报告厅申请 -->
                            <el-menu-item index="3" @click="openDialog">
                                <el-icon>
                                    <DocumentAdd />
                                </el-icon>
                                <template #title>报告厅申请</template>
                            </el-menu-item>
                            <!-- 流程审批 -->
                            <el-menu-item index="4">
                                <el-icon>
                                    <Document />
                                </el-icon>
                                <template #title>流程审批</template>
                            </el-menu-item>
                        </el-menu>
                    </el-aside>

                    <el-main>
                        <!-- 首页内容 -->
                        <el-card class="box-card_1" v-if="activeIndex === '1'">
                            <!-- 事件触发时更新 RepairTable -->
                            <Repair-table :tableData="tableData"></Repair-table>
                        </el-card>

                        <!-- 设备报修内容 -->
                        <el-card class="box-card" v-if="activeIndex === '2'">
                            <!-- 关闭对话框后的内容写在这里 -->
                            <el-card align-center>
                                <SubmitForm @form-submitted="fetchRepairsData"></SubmitForm>
                            </el-card>
                            <el-dialog v-model="DialogVisible" title="设备报修申请" width="40%" align-center>
                                <!-- 监听 SubmitForm 组件的自定义事件 -->
                                <SubmitForm @form-submitted="fetchRepairsData"></SubmitForm>
                                <template #footer><span class="dialog-footer"></span></template>
                            </el-dialog>
                        </el-card>

                        <!-- 报告厅申请内容 -->
                        <el-card class="box-card" v-if="activeIndex === '3'">
                            <!-- 关闭对话框后的内容写在这里 -->
                            <el-card align-center>
                                <LecturehallApply></LecturehallApply>
                            </el-card>
                            <el-dialog v-model="DialogVisible" title="报告厅申请" width="40%" align-center>
                                <LecturehallApply></LecturehallApply>
                                <template #footer><span class="dialog-footer"></span></template>
                            </el-dialog>
                        </el-card>

                        <!-- 流程审批内容 -->
                        <div class="box-card" v-if="activeIndex === '4'">
                            <ProcessApproval :tableData="tableData"></ProcessApproval>
                        </div>

                    </el-main>

                </el-container>
            </div>
        </div>

    </view-box>
</template>

<style scoped>
view-box {
    margin: 0 auto;
    width: 100%;
    height: auto;
    margin-top: 150px;
    display: flex;
    justify-content: space-around
}

/* 主盒子布局 */
.main-box {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 70vh;
}

.main-box:before {
    position: absolute;
    z-index: -1;
    content: "";
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: space-around;
    background: #eef2f7;
}

/* 内容区域 */
aside.el-aside {
    width: 200px;
    height: 650px;
    padding-top: 20px;
    background: white;
    border-radius: 12px 0px 0px 12px;
    box-shadow: 0 6px 6px 0 rgba(0, 0, 0, 0.18);
    z-index: 1;
}

main.el-main {
    width: 1462px;
    height: 650px;
    background: rgb(255, 255, 255);
    border-radius: 0px 12px 12px 0px;
    box-shadow: 0 6px 6px 0 rgba(0, 0, 0, 0.18);
}

/* el-card布局 */
.box-card {
    height: 600px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.box-card_1 {
    height: 600px;
}

.box-card .el-card {
    background: rgb(246, 246, 246);
    margin-left: -150px;
    width: 30vw;
    height: 30vh;
}

.table-with-fixed-height {
    height: 450px;
    overflow-y: auto;
}

.card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
}
</style>

<script lang="ts" setup>
import { ref, onMounted } from 'vue'
import {
    Document,
    Menu as IconMenu,
    Grid,
    DocumentAdd,
    Help,
} from '@element-plus/icons-vue'
import apiClient from "../apiClient";

const DialogVisible = ref(false)
const openDialog = () => {
    DialogVisible.value = true;
}


const tableData = ref([]); // 添加 tableData 变量
const fetchRepairsData = async () => {
    try {
        const response = await apiClient.get('/api/repairs');
        tableData.value = response.data;
    } catch (error) {
        console.error('Error fetching repairs data:', error);
    }
};
onMounted(fetchRepairsData);

// elementplus组件
const isCollapse = ref(false)
const handleOpen = (key: string, keyPath: string[]) => {
    console.log(key, keyPath)
}
const handleClose = (key: string, keyPath: string[]) => {
    console.log(key, keyPath)
}


// const tableData = [
//     { },
// ]


const activeIndex = ref('1') // 添加 activeIndex 变量，默认设置为 '1'
const handleSelect = (index: string) => {  // 添加 handleSelect 方法
    activeIndex.value = index
}

</script>

<script lang="ts">
import SubmitForm from './SubmitForm.vue';
import RepairTable from './RepairTable.vue';
import LecturehallApply from './LecturehallApply.vue';
import ProcessApproval from './ProcessApproval.vue';

export default {
    name: 'ProductsView',
    components: {
        SubmitForm,
        RepairTable,
        LecturehallApply,
        ProcessApproval,
    },
};
</script>