<script setup lang="ts">
import { Card, Typography, Row, Col, Divider, List, Tag } from 'ant-design-vue'
import { CheckCircleOutlined, StarOutlined, TeamOutlined, RocketOutlined } from '@ant-design/icons-vue'

const { Title, Paragraph } = Typography
</script>

<template>
  <div class="about">
    <!-- 页面标题 -->
    <Card class="page-header">
      <Title :level="2">关于 Vue ReadClass</Title>
      <Paragraph>
        Vue ReadClass是一个现代化的Vue.js学习平台，致力于为开发者提供最优质的学习体验。
      </Paragraph>
    </Card>

    <!-- 平台特色 -->
    <Row :gutter="[24, 24]" class="feature-row">
      <Col :xs="24" :lg="12">
      <Card title="我们的使命" class="mission-card">
        <Paragraph>
          我们致力于为Vue.js开发者提供最全面、最实用的学习资源。通过精心设计的学习路径、
          丰富的实践项目和活跃的社区支持，帮助每一位学习者快速掌握Vue.js开发技能。
        </Paragraph>
        <List :data-source="[
          '提供最新的Vue.js技术栈学习资源',
          '设计循序渐进的学习路径',
          '提供丰富的实践项目',
          '建立活跃的学习社区'
        ]">
          <template #renderItem="{ item }">
            <List.Item>
              <CheckCircleOutlined style="color: #52c41a; margin-right: 8px;" />
              {{ item }}
            </List.Item>
          </template>
        </List>
      </Card>
      </Col>

      <Col :xs="24" :lg="12">
      <Card title="技术栈" class="tech-card">
        <div class="tech-tags">
          <Tag color="blue">Vue 3</Tag>
          <Tag color="green">Composition API</Tag>
          <Tag color="orange">Vite</Tag>
          <Tag color="purple">TypeScript</Tag>
          <Tag color="cyan">Pinia</Tag>
          <Tag color="magenta">Vue Router</Tag>
          <Tag color="red">Ant Design Vue</Tag>
          <Tag color="volcano">ESLint</Tag>
        </div>
        <Divider />
        <Paragraph>
          我们使用最新的前端技术栈，确保学习内容的前沿性和实用性。
          所有代码示例都经过精心编写和测试，可以直接在实际项目中使用。
        </Paragraph>
      </Card>
      </Col>
    </Row>

    <!-- 团队介绍 -->
    <Card title="我们的团队" class="team-card">
      <Row :gutter="[24, 24]">
        <Col :xs="24" :sm="12" :lg="8">
        <div class="team-member">
          <div class="member-avatar">
            <TeamOutlined />
          </div>
          <Title :level="4">开发团队</Title>
          <Paragraph>
            由经验丰富的Vue.js开发者组成，致力于提供高质量的学习内容和技术支持。
          </Paragraph>
        </div>
        </Col>

        <Col :xs="24" :sm="12" :lg="8">
        <div class="team-member">
          <div class="member-avatar">
            <StarOutlined />
          </div>
          <Title :level="4">内容团队</Title>
          <Paragraph>
            专业的技术写作团队，确保学习内容的准确性和易理解性。
          </Paragraph>
        </div>
        </Col>

        <Col :xs="24" :sm="12" :lg="8">
        <div class="team-member">
          <div class="member-avatar">
            <RocketOutlined />
          </div>
          <Title :level="4">产品团队</Title>
          <Paragraph>
            专注于用户体验设计，打造最优质的学习平台。
          </Paragraph>
        </div>
        </Col>
      </Row>
    </Card>

    <!-- 联系我们 -->
    <Card title="联系我们" class="contact-card">
      <Row :gutter="24">
        <Col :span="12">
        <Paragraph>
          <strong>邮箱：</strong> contact@vuereadclass.com
        </Paragraph>
        <Paragraph>
          <strong>GitHub：</strong> github.com/vuereadclass
        </Paragraph>
        </Col>
        <Col :span="12">
        <Paragraph>
          <strong>社区：</strong> discord.gg/vuereadclass
        </Paragraph>
        <Paragraph>
          <strong>文档：</strong> docs.vuereadclass.com
        </Paragraph>
        </Col>
      </Row>
    </Card>
  </div>
</template>

<style scoped>
.about {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
  box-sizing: border-box;
}

.page-header {
  margin-bottom: 24px;
  text-align: center;
}

.feature-row {
  margin-bottom: 24px;
}

.mission-card,
.tech-card {
  height: 100%;
}

.tech-tags {
  margin-bottom: 16px;
}

.tech-tags .ant-tag {
  margin-bottom: 8px;
  font-size: 14px;
  padding: 4px 12px;
}

.team-card {
  margin-bottom: 24px;
}

.team-member {
  text-align: center;
  padding: 20px;
}

.member-avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 16px;
  font-size: 32px;
  color: white;
}

.contact-card {
  margin-bottom: 24px;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .about {
    padding: 0 16px;
  }
  
  .page-header {
    margin-bottom: 16px;
  }
  
  .feature-row {
    margin-bottom: 16px;
  }
  
  .team-member {
    padding: 16px;
  }
  
  .member-avatar {
    width: 60px;
    height: 60px;
    font-size: 24px;
    margin-bottom: 12px;
  }
  
  .tech-tags .ant-tag {
    font-size: 12px;
    padding: 2px 8px;
  }
  
  .contact-card {
    margin-bottom: 16px;
  }
}

@media (max-width: 480px) {
  .about {
    padding: 0 12px;
  }
  
  .page-header {
    margin-bottom: 12px;
  }
  
  .feature-row {
    margin-bottom: 12px;
  }
  
  .team-member {
    padding: 12px;
  }
  
  .member-avatar {
    width: 50px;
    height: 50px;
    font-size: 20px;
    margin-bottom: 8px;
  }
  
  .tech-tags .ant-tag {
    font-size: 11px;
    padding: 1px 6px;
  }
  
  .contact-card {
    margin-bottom: 12px;
  }
}

/* 超小屏幕适配 */
@media (max-width: 360px) {
  .about {
    padding: 0 8px;
  }
  
  .team-member {
    padding: 8px;
  }
  
  .member-avatar {
    width: 40px;
    height: 40px;
    font-size: 16px;
    margin-bottom: 6px;
  }
  
  .tech-tags .ant-tag {
    font-size: 10px;
    padding: 1px 4px;
  }
}
</style>
