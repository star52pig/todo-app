<template>
    <el-row :gutter="20">
        <el-col :span="22">
            <el-input v-model="inputText" placeholder="請輸入旅遊景點" @keyup.enter="addEntry"></el-input>
        </el-col>
        <el-col :span="2">
            <el-button type="primary" @click="addEntry">
                新增
            </el-button>
        </el-col>
    </el-row>
</template>
  
<script>
import { ref } from 'vue';

export default {
    name: 'AddPlaces',
    setup(_, { emit }) {
        const inputText = ref('');

        const addEntry = () => {
            if (inputText.value.trim()) {
                emit('add-entry', inputText.value);
                inputText.value = '';
            }
        };

        return { inputText, addEntry };
    },
};
</script>