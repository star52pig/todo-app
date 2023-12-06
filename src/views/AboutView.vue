<template>
  <div class="about">
    <el-card>
      <el-row>
        <el-col :span="12">
          <h1>關於我們</h1>
          <p>{{ aboutText }}</p>
        </el-col>

        <el-col :span="12">
          <div class="features">
            <h2>我們的特色</h2>
            <el-timeline v-for="(item, index) in features" :key="index">
              <el-timeline-item
                :timestamp="item.title"
                :color="item.color"
              >
                {{ item.content }}
              </el-timeline-item>
            </el-timeline>
          </div>
        </el-col>
      </el-row>
    </el-card>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'AboutView',
  setup() {
    const aboutText = ref('我們是一家專業的旅行社，為您提供最優質的旅遊體驗和度假套餐。');
    const features = ref([
      {
        title: '量身定制的行程',
        content:
          '我們擁有一支專業的團隊，根據您的喜好和需求，為您打造獨一無二的旅行體驗。',
        color: '#3AA0FF',
      },
      {
        title: '多元化的目的地選擇',
        content:
          '從亞洲的熱帶風情、歐洲的歷史古城，到美洲的壯觀自然景觀，我們提供多樣化的目的地以滿足您的各種需求。',
        color: '#F56C6C',
      },
      {
        title: '優質的合作伙伴',
        content:
          '我們與知名的交通運輸公司、當地向導服務和酒店業配合，讓您在旅行中享受高品質的服務。',
        color: '#67C23A',
      },
      {
        title: '親切的客戶服務',
        content:
          '我們的客服團隊隨時為您解答疑惑，協助您解決旅行中遇到的問題。',
        color: '#E6A23C',
      },
    ]);

    return { aboutText, features };
  },
};
</script>

<style scoped>
.about {
  font-family: Arial, sans-serif;
  color: #333;
}

.about h1 {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 16px;
}

.about p {
  font-size: 16px;
  line-height: 1.5;
}

.features h2 {
  font-size: 20px;
  font-weight: bold;
  margin-top: 32px;
  margin-bottom: 12px;
}
</style>