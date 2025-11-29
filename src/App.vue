<script setup>
import { ref } from 'vue'
import { Button, Card, Typography, Space, Steps } from 'ant-design-vue'
import { DownloadOutlined, CheckCircleOutlined } from '@ant-design/icons-vue'

const { Title, Paragraph, Text, Link } = Typography
const { Step } = Steps
const downloadUrl = '/download/resume-extension.zip'

const handleDownload = () => {
  const link = document.createElement('a')
  link.href = downloadUrl
  link.download = 'resume-extension.zip'
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
  console.log('下载已开始，请按照指引安装扩展！')
}

// 4个功能点
const featureList = [
  {
    title: '一键自动填写',
    desc: '智能识别表单，点击一次即可完成90%的填写工作，大幅提升投递效率。',
    src: 'https://placehold.co/800x450/E6F4FF/1890ff?text=Wide+Image+16:9',
    type: 'wide' 
  },
  {
    title: '多模型切换',
    desc: '内置多种填写策略，灵活应对不同网站。',
    src: 'model_change.gif',
    type: 'narrow' 
  },
  {
    title: '数据隐私安全',
    desc: '所有数据仅存储在本地，绝不上传云端，全方位保障您的隐私安全。',
    src: 'https://placehold.co/400x450/E6F4FF/1890ff?text=Narrow+Image',
    type: 'narrow'
  },
  {
    title: '智能文本补全',
    desc: '在填写自我评价或项目经历时，提供AI辅助写作与润色建议，让简历更出彩。',
    src: 'https://placehold.co/800x450/E6F4FF/1890ff?text=Wide+Image+16:9',
    type: 'wide'
  }
]

const versions = [
  {
    version: '1.0.0',
    date: '2024-11-01',
    features: ['初始版本', '支持简历自动填写', 'Chrome浏览器支持']
  },
  {
    version: '1.1.0',
    date: '2024-11-15',
    features: ['优化填写速度', '增加表单适配', '修复已知问题']
  },
  {
    version: '1.2.0',
    date: '2024-12-01',
    features: ['添加多种简历模板', '支持自定义字段映射', '增强数据安全性']
  }
]
</script>

<template>
  <div class="app-container">
    <div class="light-flow-effect"></div>

    <!-- 背景装饰球 -->
    <div class="bg-decoration ball-1"></div>
    <div class="bg-decoration ball-2"></div>
    <div class="bg-decoration ball-3"></div> 

    <!-- 头部区域 -->
    <header class="header-section">
      <div class="logo-container">
        <img src="/logo.png" alt="简历自动填写助手" class="app-logo" />
      </div>
      <div class="header-content">
        <Title :level="1" class="app-title">简历自动填写助手</Title>
        <Paragraph class="app-description">
          一款高效的Chrome浏览器扩展，让您的简历填写过程变得简单快捷
        </Paragraph>
        <Button 
          type="primary" 
          size="large" 
          class="download-button"
          @click="handleDownload"
        >
          <template #icon><DownloadOutlined /></template>
          快速开始
        </Button>
      </div>
    </header>

    <main class="main-content">
      <!-- 核心功能区域 -->
      <section class="section-block intro-section">
        <div class="section-header">
           <Title :level="2" class="section-title">核心功能</Title>
           <Paragraph class="intro-description">
            告别繁琐的重复填写，体验智能化的求职新方式
          </Paragraph>
        </div>

        <div class="feature-grid">
          <div 
            v-for="(item, index) in featureList" 
            :key="index" 
            class="feature-card"
            :class="{ 
              'card-wide': index === 0 || index === 3, 
              'card-narrow': index === 1 || index === 2 
            }"
          >
            <div class="card-text">
              <h3 class="card-title">{{ item.title }}</h3>
              <p class="card-desc">{{ item.desc }}</p>
            </div>
            <div class="card-visual">
              <img :src="item.src" :alt="item.title" class="card-img" />
            </div>
          </div>
        </div>
      </section>

      <!-- 统计数据 -->
      <section class="section-block">
        <Card class="content-card stats-card" :bordered="false">
          <div class="plugin-stats">
            <div class="stat-item">
              <span class="stat-number">1000+</span>
              <span class="stat-label">用户正在使用</span>
            </div>
            <div class="stat-item">
              <span class="stat-number">50+</span>
              <span class="stat-label">支持的招聘网站</span>
            </div>
            <div class="stat-item">
              <span class="stat-number">95%</span>
              <span class="stat-label">自动填写准确率</span>
            </div>
            <div class="stat-item">
              <span class="stat-number">2.5h/周</span>
              <span class="stat-label">平均节省时间</span>
            </div>
          </div>
        </Card>
      </section>

      <!-- 使用指南 (已更新为截图内容) -->
      <section class="section-block guide-section">
        <Card class="content-card guide-card">
          <Title :level="2" class="section-title">使用指南</Title>
          <Paragraph class="intro-description">
            简历自动填写助手操作简单，只需几步即可开始使用。按照以下步骤操作，轻松提高您的求职效率。
          </Paragraph>
          
          <div class="steps-container">
            <!-- 步骤 1 -->
            <div class="step-item">
              <div class="step-number">1</div>
              <div class="step-content">
                <h3 class="step-title">安装Chrome扩展</h3>
                <div class="step-description">
                  <ol>
                    <li>点击上方的"快速开始"按钮，下载扩展文件</li>
                    <li>在Chrome浏览器中输入 <code>chrome://extensions/</code> 打开扩展管理页面</li>
                    <li>开启页面右上角的"开发者模式"开关</li>
                    <li>将下载的zip文件拖拽到扩展管理页面中</li>
                    <li>在弹出的确认对话框中点击"添加扩展程序"</li>
                  </ol>
                </div>
              </div>
            </div>
            
            <!-- 连接线 -->
            <div class="step-divider"></div>
            
            <!-- 步骤 2 -->
            <div class="step-item">
              <div class="step-number">2</div>
              <div class="step-content">
                <h3 class="step-title">配置您的简历信息</h3>
                <div class="step-description">
                  <ol>
                    <li>点击Chrome浏览器工具栏中的插件图标</li>
                    <li>在弹出的界面中选择"编辑个人信息"</li>
                    <li>完整填写您的个人基本信息、联系方式</li>
                    <li>添加您的教育背景、工作经历、项目经验</li>
                  </ol>
                  <!-- 提示框 -->
                  <div class="tip-text">
                    💡 提示：您可以创建多个简历模板，针对不同类型的职位进行定制。
                  </div>
                </div>
              </div>
            </div>
            
            <!-- 连接线 -->
            <div class="step-divider"></div>
            
            <!-- 步骤 3 -->
            <div class="step-item">
              <div class="step-number">3</div>
              <div class="step-content">
                <h3 class="step-title">开始自动填写简历</h3>
                <div class="step-description">
                  <ol>
                    <li>访问您喜欢的招聘网站（如智联招聘、前程无忧等）</li>
                    <li>导航到简历填写或投递页面</li>
                    <li>点击Chrome工具栏中的插件图标</li>
                    <li>选择"自动填写简历"选项</li>
                  </ol>
                </div>
              </div>
            </div>
          </div>
        </Card>
      </section>

      <!-- 版本信息 -->
      <section class="section-block version-section">
        <Card class="content-card version-card">
          <Title :level="2" class="section-title">版本信息</Title>
          <div class="version-timeline">
            <div v-for="(version, index) in versions" :key="index" class="version-item">
              <div class="version-header">
                <div class="version-badge" :class="{ 'latest': index === 0 }">
                  {{ version.version }} <span v-if="index === 0" class="latest-badge">最新</span>
                </div>
                <div class="version-date">{{ version.date }}</div>
              </div>
              <div class="version-changes">
                <div class="changes-list">
                  <div v-for="(feature, i) in version.features" :key="i" class="change-item">
                    <span class="change-icon"><CheckCircleOutlined /></span>
                    <span class="change-text">{{ feature }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </Card>
      </section>
    </main>

    <footer class="footer-section">
      <Text type="secondary">© 2024 简历自动填写助手 | Chrome浏览器扩展</Text>
    </footer>
  </div>
</template>

<style scoped>
/* =========================================
   1. 背景与容器
   ========================================= */
.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  position: relative;
  background: linear-gradient(180deg, #e6f4ff 0%, #f0f7ff 50%, #f4f6f8 100%);
  overflow-x: hidden;
}

.bg-decoration {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  z-index: 0;
  pointer-events: none;
}
.ball-1 { width: 600px; height: 600px; background: rgba(24, 144, 255, 0.08); top: -200px; left: -200px; }
.ball-2 { width: 500px; height: 500px; background: rgba(54, 207, 201, 0.08); bottom: 10%; right: -200px; }
.ball-3 { width: 400px; height: 400px; background: rgba(24, 144, 255, 0.05); top: 40%; left: -100px; }

.light-flow-effect {
  position: fixed;
  top: 0;
  left: -100%;
  width: 300%;
  height: 100%;
  background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.3) 50%, rgba(255, 255, 255, 0) 100%);
  animation: lightFlow 12s infinite linear;
  pointer-events: none;
  z-index: 1;
}

@keyframes lightFlow {
  0% { transform: translateX(-50%); }
  100% { transform: translateX(50%); }
}

.main-content {
  width: 100%;
  max-width: 1280px; 
  padding: 0 24px 60px;
  position: relative;
  z-index: 2;
}

.header-section {
  width: 100%;
  padding: 100px 20px 60px;
  text-align: center;
  position: relative;
  z-index: 2;
}

.app-logo { width: 120px; height: 120px; border-radius: 24px; box-shadow: 0 10px 40px rgba(24, 144, 255, 0.2); transition: transform 0.3s ease; background: #fff; }
.app-logo:hover { transform: scale(1.05) rotate(2deg); }
.app-title { color: #1890ff !important; margin-top: 24px !important; font-weight: 800 !important; font-size: 40px !important; }
.app-description { font-size: 20px; color: #666; max-width: 700px; margin: 20px auto 32px; line-height: 1.6; }
.download-button { height: 56px; font-size: 18px; padding: 0 40px; border-radius: 28px; background: linear-gradient(135deg, #1890ff 0%, #36cfc9 100%); border: none; box-shadow: 0 8px 24px rgba(24, 144, 255, 0.35); display: inline-flex; align-items: center; gap: 8px; transition: all 0.3s ease; }
.download-button:hover { transform: translateY(-2px); box-shadow: 0 12px 32px rgba(24, 144, 255, 0.45); }

/* =========================================
   2. 核心功能区 (宽窄卡片)
   ========================================= */
.section-block { margin-bottom: 80px; }
.section-header { text-align: center; margin-bottom: 50px; }
.section-title::after { content: ''; display: block; width: 60px; height: 4px; background: linear-gradient(90deg, #1890ff 0%, #36cfc9 100%); margin: 16px auto 0; border-radius: 2px; }
.intro-description { text-align: center; font-size: 16px; color: #666; max-width: 800px; margin: 0 auto; line-height: 1.6; }

.feature-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); 
  gap: 24px;
  width: 100%;
}

.feature-card {
  background: #ffffff; 
  border-radius: 24px;
  overflow: hidden;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.6);
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
}

.feature-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 25px 50px rgba(24, 144, 255, 0.15);
  border-color: #1890ff;
}

.card-wide { grid-column: span 2; }
.card-narrow { grid-column: span 1; }
.card-text { padding: 32px 32px 20px; }
.card-title { font-size: 24px; font-weight: 700; color: #1f1f1f; margin-bottom: 12px; }
.card-desc { font-size: 16px; color: #666; line-height: 1.6; }
.card-visual { flex: 1; display: flex; align-items: flex-end; justify-content: center; background: linear-gradient(to bottom, #ffffff 0%, #f0f7ff 100%); padding: 20px 30px 0 30px; overflow: hidden; }
.card-img { width: 100%; height: auto; display: block; transition: transform 0.5s ease; border-radius: 12px 12px 0 0; box-shadow: 0 -8px 24px rgba(24, 144, 255, 0.12); }
.feature-card:hover .card-img { transform: scale(1.02); }

@media (max-width: 900px) {
  .feature-grid { grid-template-columns: 1fr; }
  .card-wide, .card-narrow { grid-column: span 1; }
  .main-content { padding: 0 16px 40px; }
}

/* =========================================
   3. 其他内容样式 (Guide, Stats, Version)
   ========================================= */
.content-card { 
  border-radius: 24px; 
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.04); 
  border: 1px solid rgba(255, 255, 255, 0.8); 
  background: #ffffff; 
}

.stats-card { background: linear-gradient(135deg, #ffffff 0%, #f7fcff 100%); }
.plugin-stats { display: flex; justify-content: space-around; flex-wrap: wrap; gap: 20px; }
.stat-item { text-align: center; flex: 1; min-width: 140px; }
.stat-number { display: block; font-size: 36px; font-weight: 800; color: #1890ff; font-family: Arial, sans-serif; margin-bottom: 4px; }
.stat-label { color: #666; font-size: 14px; font-weight: 500; }

/* 步骤条特定样式 - 适配截图 */
.steps-container { padding: 30px 40px; }
.step-item { display: flex; gap: 24px; margin-bottom: 0; }
.step-number { 
  flex-shrink: 0; 
  width: 50px; 
  height: 50px; 
  border-radius: 50%; 
  background: linear-gradient(135deg, #2db7f5 0%, #1890ff 100%); 
  color: white; 
  display: flex; 
  align-items: center; 
  justify-content: center; 
  font-size: 24px; 
  font-weight: 700; 
  box-shadow: 0 8px 20px rgba(24, 144, 255, 0.25); 
  z-index: 2;
  position: relative;
}
.step-content { flex: 1; padding-top: 5px; }
.step-title { font-size: 20px; font-weight: 700; color: #1f1f1f; margin-bottom: 15px; }
.step-description { color: #555; line-height: 1.8; font-size: 15px; }
.step-description ol { padding-left: 20px; margin: 0; list-style-type: decimal; }
.step-description li { margin-bottom: 8px; }
.step-description code { background: #fff0f6; border: 1px solid #ffadd2; padding: 2px 6px; border-radius: 4px; color: #c41d7f; font-family: monospace; font-size: 13px; }

/* 提示框样式 */
.tip-text {
  background: #e6f7ff;
  border: 1px solid #91d5ff;
  padding: 16px 20px;
  border-radius: 8px;
  margin-top: 15px;
  color: #0050b3;
  font-size: 14px;
  font-weight: 500;
  display: flex;
  align-items: center;
  gap: 8px;
}

/* 垂直连接线样式 */
.step-divider { 
  width: 2px; 
  height: 50px; 
  background: #e8e8e8; 
  margin: 5px 0 5px 24px; /* 对齐圆圈中心 */
}

/* 版本信息样式 */
.version-timeline { padding: 10px 20px; }
.version-item { padding-bottom: 30px; border-bottom: 1px solid #f0f0f0; margin-bottom: 30px; }
.version-item:last-child { border-bottom: none; margin-bottom: 0; }
.version-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px; }
.version-badge { background: #f0f2f5; color: #595959; padding: 4px 12px; border-radius: 100px; font-weight: 600; display: inline-flex; align-items: center; gap: 8px; }
.version-badge.latest { background: #e6f7ff; color: #1890ff; border: 1px solid #91d5ff; }
.latest-badge { background: #1890ff; color: white; font-size: 12px; padding: 1px 6px; border-radius: 4px; }
.change-item { display: flex; align-items: flex-start; gap: 10px; margin-bottom: 8px; line-height: 1.6; color: #555; }
.change-icon { color: #52c41a; margin-top: 3px; }
.footer-section { padding: 0 20px 40px; text-align: center; color: #999; position: relative; z-index: 2; }
</style>