<template>
    <el-table :data="tableData" style="margin-top: 20px; width: 100%;">
        <el-table-column label="索引" width="100">
            <template #default="{ $index }">
                {{ $index + 1 }}
            </template>
        </el-table-column>
        <el-table-column label="Input" width="120">
            <template #default="scope">
                <el-checkbox v-model="scope.row.checked"></el-checkbox>
            </template>
        </el-table-column>
        <el-table-column label="Text" width="750">
            <template #default="scope">
                <div v-if="!scope.row.editing">
                    <label :style="{ textDecoration: scope.row.checked ? 'line-through' : 'none' }">
                        {{ scope.row.input }}
                    </label>
                </div>
                <div v-else>
                    <el-input v-model="scope.row.editValue"></el-input>
                </div>
            </template>
        </el-table-column>
        <el-table-column label="操作">
            <template #default="scope">                
                <el-button type="primary" @click="startEdit(scope.$index)" v-if="!scope.row.editing">編輯</el-button>
                <el-button type="success" @click="saveEdit(scope.$index)" v-if="scope.row.editing">保存</el-button>
                <el-button type="danger" @click="removeEntry(scope.$index)">刪除</el-button>
            </template>
        </el-table-column>
    </el-table>
</template>
  
<script>
import { reactive } from 'vue';

export default {
    name: 'Item',
    props: {
        tableData: {
            type: Array,
            required: true
        }
    },
    setup(props) {
        const state = reactive({
            data: props.tableData
        });

        const removeEntry = (index) => {
            state.data.splice(index, 1);
        };

        const startEdit = (index) => {
            state.data[index].editing = true;
            state.data[index].editValue = state.data[index].input;
        };

        const saveEdit = (index) => {
            state.data[index].editing = false;
            state.data[index].input = state.data[index].editValue;
        };

        return { state, removeEntry, startEdit, saveEdit };
    }
};
</script>