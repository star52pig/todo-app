<template>
  <div class="contact">
    <h1>Contact Us</h1>
    <el-card class="form-card">
      <el-form @submit.native.prevent="submitForm" ref="contactForm" :model="contactInfo" label-width="120px">
        <el-form-item label="Your Email" prop="email" :rules="{ required: true, type: 'email', message: '请输入有效的邮箱地址', trigger: 'blur' }">
          <el-input v-model="contactInfo.email"></el-input>
        </el-form-item>
        <el-form-item label="Your Message" prop="message" :rules="{ required: true, message: '请输入你的留言', trigger: 'blur' }">
          <el-input type="textarea" v-model="contactInfo.message"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" native-type="submit">Send</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  name: 'ContactView',
  setup() {
    const contactForm = ref(null);
    const contactInfo = reactive({ email: '', message: '' });

    const submitForm = () => {
      contactForm.value.validate((valid) => {
        if (valid) {
          console.log(contactInfo);
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    };

    return { contactForm, contactInfo, submitForm };
  },
};
</script>

<style scoped>
.contact {
  display: flex;
  flex-direction: column;
  align-items: center;
  /* justify-content: center; */
  height: 100vh;
  background-color: #f5f7fa;
}

h1 {
  margin-bottom: 20px;
  font-size: 36px;
  font-weight: bold;
  color: #323233;
}

.form-card {
  width: 60%;
  padding: 20px;
}

@media (max-width: 768px) {
  .form-card {
    width: 90%;
  }
}
</style>