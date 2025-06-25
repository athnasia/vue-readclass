<script setup lang="ts">
import { ref } from 'vue'
import { Card, Row, Col, Typography, Carousel, Button } from 'ant-design-vue'
import { BookOutlined, ReadOutlined, FileTextOutlined, EditOutlined } from '@ant-design/icons-vue'

const { Title, Paragraph } = Typography

// 轮播图片数据
const carouselImages = [
  new URL('@/assets/banner/banner1.png', import.meta.url).href,
  new URL('@/assets/banner/banner2.png', import.meta.url).href,
  new URL('@/assets/banner/banner3.png', import.meta.url).href
]

// 导航菜单项
const menuItems = [
  {
    key: 'materials',
    icon: BookOutlined,
    label: '六维素材库',
    description: '丰富的阅读素材资源',
    detail: '六维素材库为您提供多维度、分主题、分难度的优质阅读素材，涵盖文学、科技、社会、历史等多个领域，助力学生拓展知识面、提升阅读兴趣。'
  },
  {
    key: 'textbook',
    icon: ReadOutlined,
    label: '教材精读',
    description: '深度解析教材内容',
    detail: '教材精读模块带您逐章逐节精读教材，配合重点难点讲解、知识点梳理和配套练习，帮助学生夯实基础、突破难点。'
  },
  {
    key: 'exam',
    icon: FileTextOutlined,
    label: '应试阅读',
    description: '针对性阅读训练',
    detail: '应试阅读模块针对各类考试题型，提供真题演练、解题技巧、时间管理等专项训练，提升学生应试能力和解题速度。'
  },
  {
    key: 'writing',
    icon: EditOutlined,
    label: '写作微技巧',
    description: '提升写作能力',
    detail: '写作微技巧模块涵盖写作思路、结构布局、语言表达、常见错误分析等内容，帮助学生写出高分作文。'
  }
]

// 当前悬停的卡片索引
const hoverIndex = ref(-1)
</script>

<template>
  <main class="home-page">
    <!-- 图片轮播 -->
    <div class="carousel-section">
      <Carousel autoplay class="main-carousel">
        <div v-for="(image, index) in carouselImages" :key="index" class="carousel-item">
          <img :src="image" :alt="`轮播图片 ${index + 1}`" class="carousel-image" />
        </div>
      </Carousel>
    </div>

    <!-- 功能导航卡片 -->
    <div class="features-section">
      <Title :level="2" class="section-title">核心功能</Title>
      <Row :gutter="16" class="features-grid">
        <Col :xs="24" :sm="12" :lg="6" v-for="(item, idx) in menuItems" :key="item.key">
        <Card hoverable class="feature-card no-margin" @mouseenter="hoverIndex = idx" @mouseleave="hoverIndex = -1">
          <div class="feature-icon">
            <component :is="item.icon" />
          </div>
          <div class="feature-content">
            <template v-if="hoverIndex === idx">
              <div class="feature-detail">{{ item.detail }}</div>
            </template>
            <template v-else>
              <div class="feature-title">{{ item.label }}</div>
              <div class="feature-desc">{{ item.description }}</div>
            </template>
          </div>
        </Card>
        </Col>
      </Row>
    </div>

    <!-- 课程介绍 -->
    <div class="course-intro">
      <Card class="intro-card no-margin">
        <Row :gutter="0" align="middle">
          <Col :span="13">
          <Title :level="4" class="intro-title">关于唐老师的高阶阅读课</Title>
          <Paragraph class="intro-text">
            致力于培养学生深度阅读能力和批判性思维。通过四大模块，帮助学生建立系统的阅读体系。
          </Paragraph>
          <Button type="link" size="small">了解更多</Button>
          </Col>
          <Col :span="11" class="intro-image">
          <img src="https://via.placeholder.com/350x160/1890ff/ffffff?text=课程特色" alt="课程特色" />
          </Col>
        </Row>
      </Card>
    </div>
  </main>
</template>

<style scoped>
.home-page {
  min-height: 100vh;
  background: none;
  width: 100vw;
  padding: 0;
  box-sizing: border-box;
}

.carousel-section {
  width: 100vw;
  padding: 0 32px;
  box-sizing: border-box;
  margin-top: 32px;
  margin-bottom: 18px;
}

.main-carousel {
  border-radius: 24px;
  overflow: hidden;
  box-shadow: 0 6px 32px rgba(0, 0, 0, 0.13);
}

.carousel-item {
  height: 380px;
}

.carousel-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 24px;
}

.features-section {
  width: 100vw;
  padding: 0 32px;
  box-sizing: border-box;
  margin-bottom: 12px;
}

.section-title {
  text-align: center;
  margin-bottom: 24px !important;
  color: #222;
  font-size: 32px;
  font-weight: bold;
  letter-spacing: 2px;
}

.features-grid {
  margin-bottom: 0;
}

.feature-card {
  height: 220px;
  text-align: center;
  cursor: pointer;
  transition: all 0.25s cubic-bezier(.4, 2, .6, 1);
  border-radius: 18px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: #fafdff;
  box-shadow: 0 2px 12px rgba(24, 144, 255, 0.07);
  border: none;
}

.feature-card:hover {
  transform: translateY(-8px) scale(1.03);
  box-shadow: 0 8px 32px rgba(24, 144, 255, 0.18);
  background: #f0f7ff;
}

.feature-icon {
  font-size: 54px;
  color: #1890ff;
  margin-bottom: 18px;
  margin-top: 10px;
}

.feature-content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.feature-title {
  font-size: 22px;
  font-weight: 700;
  color: #222;
  margin-bottom: 8px;
}

.feature-desc {
  color: #666;
  font-size: 16px;
  font-weight: 400;
}

.no-margin {
  margin: 0 !important;
}

.course-intro {
  width: 100vw;
  padding: 0 32px 24px 32px;
  box-sizing: border-box;
}

.intro-card {
  border-radius: 14px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
  padding: 8px 0;
}

.intro-title {
  font-size: 20px;
  margin-bottom: 8px !important;
  font-weight: bold;
}

.intro-text {
  font-size: 15px;
  line-height: 1.7;
  color: #666;
  margin-bottom: 8px;
}

.intro-image img {
  width: 100%;
  border-radius: 8px;
  max-width: 350px;
  height: 160px;
  object-fit: cover;
}

.feature-detail {
  color: #1890ff;
  font-size: 16px;
  line-height: 1.7;
  padding: 0 8px;
  text-align: center;
  font-weight: 500;
  transition: color 0.2s;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .carousel-section {
    padding: 0 16px;
    margin-top: 16px;
    margin-bottom: 12px;
  }
  
  .carousel-item {
    height: 200px;
  }
  
  .main-carousel {
    border-radius: 16px;
  }
  
  .carousel-image {
    border-radius: 16px;
  }
  
  .features-section {
    padding: 0 16px;
    margin-bottom: 8px;
  }
  
  .section-title {
    font-size: 24px;
    margin-bottom: 16px !important;
    letter-spacing: 1px;
  }
  
  .feature-card {
    height: 160px;
    border-radius: 12px;
  }
  
  .feature-icon {
    font-size: 36px;
    margin-bottom: 12px;
    margin-top: 8px;
  }
  
  .feature-title {
    font-size: 16px;
    margin-bottom: 6px;
  }
  
  .feature-desc {
    font-size: 14px;
  }
  
  .feature-detail {
    font-size: 14px;
    padding: 0 4px;
  }
  
  .course-intro {
    padding: 0 16px 16px 16px;
  }
  
  .intro-card {
    border-radius: 12px;
  }
  
  .intro-title {
    font-size: 18px;
  }
  
  .intro-text {
    font-size: 14px;
  }
  
  .intro-image img {
    height: 120px;
  }
}

@media (max-width: 480px) {
  .carousel-section {
    padding: 0 12px;
    margin-top: 12px;
    margin-bottom: 8px;
  }
  
  .carousel-item {
    height: 160px;
  }
  
  .main-carousel {
    border-radius: 12px;
  }
  
  .carousel-image {
    border-radius: 12px;
  }
  
  .features-section {
    padding: 0 12px;
    margin-bottom: 6px;
  }
  
  .section-title {
    font-size: 20px;
    margin-bottom: 12px !important;
  }
  
  .feature-card {
    height: 140px;
    border-radius: 10px;
  }
  
  .feature-icon {
    font-size: 32px;
    margin-bottom: 10px;
    margin-top: 6px;
  }
  
  .feature-title {
    font-size: 14px;
    margin-bottom: 4px;
  }
  
  .feature-desc {
    font-size: 12px;
  }
  
  .feature-detail {
    font-size: 12px;
    padding: 0 2px;
  }
  
  .course-intro {
    padding: 0 12px 12px 12px;
  }
  
  .intro-card {
    border-radius: 10px;
  }
  
  .intro-title {
    font-size: 16px;
  }
  
  .intro-text {
    font-size: 13px;
  }
  
  .intro-image img {
    height: 100px;
  }
}

/* 超小屏幕适配 */
@media (max-width: 360px) {
  .carousel-section {
    padding: 0 8px;
  }
  
  .carousel-item {
    height: 140px;
  }
  
  .features-section {
    padding: 0 8px;
  }
  
  .section-title {
    font-size: 18px;
  }
  
  .feature-card {
    height: 120px;
  }
  
  .feature-icon {
    font-size: 28px;
  }
  
  .feature-title {
    font-size: 13px;
  }
  
  .feature-desc {
    font-size: 11px;
  }
  
  .course-intro {
    padding: 0 8px 8px 8px;
  }
  
  .intro-image img {
    height: 80px;
  }
}
</style>
