<script setup>
import { ref } from 'vue'
import { Button, Card, Typography, Space, Steps } from 'ant-design-vue'
import { DownloadOutlined, CheckCircleOutlined } from '@ant-design/icons-vue' // 修复：补充导入 CheckCircleOutlined

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
    <!-- 流光效果背景 (放在最底层) -->
    <div class="light-flow-effect"></div>

    <!-- 头部区域 -->
    <header class="header-section">
      <div class="logo-container">
        <!-- 这里的Logo通常建议加一个占位符，防止加载失败时布局跳动 -->
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

    <!-- 主要内容区域 -->
    <main class="main-content">
      <!-- 插件介绍部分 -->
      <section class="section-block intro-section">
        <Card class="content-card intro-card">
          <Title :level="2" class="section-title">插件介绍</Title>
          <Paragraph class="intro-description">
            简历自动填写助手是一款专为求职者设计的Chrome浏览器扩展，旨在简化在各招聘网站上填写简历的繁琐过程。
            当您在多个招聘平台投递简历时，是否曾为重复填写个人信息、工作经历和教育背景而感到厌倦？
            本插件将为您解决这一痛点，让您的求职之旅更加高效顺畅。
          </Paragraph>
          
          <div class="features-grid">
            <Card class="feature-card" hoverable :bordered="false">
              <h3 class="feature-title">一键自动填写</h3>
              <p class="feature-description">只需点击一次，即可在各大招聘网站自动填写您的完整简历信息，节省大量时间。</p>
            </Card>
            
            <Card class="feature-card" hoverable :bordered="false">
              <h3 class="feature-title">多平台支持</h3>
              <p class="feature-description">支持主流招聘平台，包括智联招聘、前程无忧、拉勾网、BOSS直聘等50+个网站。</p>
            </Card>
            
            <Card class="feature-card" hoverable :bordered="false">
              <h3 class="feature-title">数据安全保障</h3>
              <p class="feature-description">所有个人信息仅存储在您的本地浏览器中，不会上传至任何服务器，确保信息安全。</p>
            </Card>
            
            <Card class="feature-card" hoverable :bordered="false">
              <h3 class="feature-title">自定义模板</h3>
              <p class="feature-description">支持创建多个简历模板，根据不同的职位需求快速切换，投递更精准。</p>
            </Card>
          </div>
          
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

      <!-- 使用指南部分 -->
      <section class="section-block guide-section">
        <Card class="content-card guide-card">
          <Title :level="2" class="section-title">使用指南</Title>
          <Paragraph class="intro-description">
            简历自动填写助手操作简单，只需几步即可开始使用。按照以下步骤操作，轻松提高您的求职效率。
          </Paragraph>
          
          <div class="steps-container">
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
            
            <div class="step-divider"></div>
            
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
                  <p class="tip-text">💡 提示：您可以创建多个简历模板，针对不同类型的职位进行定制。</p>
                </div>
              </div>
            </div>
            
            <div class="step-divider"></div>
            
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

      <!-- 版本信息部分 -->
      <section class="section-block version-section">
        <Card class="content-card version-card">
          <Title :level="2" class="section-title">版本信息</Title>
          <Paragraph class="intro-description">
            我们持续优化和更新简历自动填写助手，为用户提供更好的使用体验。
          </Paragraph>
          
          <div class="version-timeline">
            <div v-for="(version, index) in versions" :key="index" class="version-item">
              <div class="version-header">
                <div class="version-badge" :class="{ 'latest': index === 0 }">
                  {{ version.version }}
                  <span v-if="index === 0" class="latest-badge">最新</span>
                </div>
                <div class="version-date">{{ version.date }}</div>
              </div>
              
              <div class="version-changes">
                <div class="changes-list">
                  <div 
                    v-for="(feature, i) in version.features" 
                    :key="i" 
                    class="change-item"
                  >
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

    <!-- 页脚部分 -->
    <footer class="footer-section">
      <Text type="secondary">© 2024 简历自动填写助手 | Chrome浏览器扩展</Text>
    </footer>
  </div>
</template>

<style scoped>
/* =========================================
   1. 基础布局修复 (核心修复点)
   ========================================= */
.app-container {
  /* 强制重置对齐方式，防止Vue默认的居中样式导致顶部内容不可见 */
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  
  width: 100%;
  min-height: 100vh;
  position: relative;
  background: linear-gradient(135deg, #e6f4ff 0%, #f0f9ff 50%, #ffffff 100%);
  overflow-x: hidden; /* 防止水平滚动条 */
}

/* 修复流光效果，确保不遮挡点击 (pointer-events: none) */
.light-flow-effect {
  position: fixed;
  top: 0;
  left: -100%;
  width: 300%;
  height: 100%;
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(190, 224, 255, 0.2) 50%,
    rgba(255, 255, 255, 0) 100%
  );
  animation: lightFlow 10s infinite linear;
  pointer-events: none; /* 关键：让鼠标点击穿透 */
  z-index: 0;
}

@keyframes lightFlow {
  0% { transform: translateX(-50%); }
  100% { transform: translateX(50%); }
}

/* =========================================
   2. 头部样式
   ========================================= */
.header-section {
  width: 100%;
  padding: 80px 20px 60px; /* PC端保持足够的顶部间距 */
  text-align: center;
  position: relative;
  z-index: 1;
}

.app-logo {
  width: 120px;
  height: 120px;
  border-radius: 24px;
  box-shadow: 0 10px 40px rgba(24, 144, 255, 0.2);
  transition: transform 0.3s ease;
  background: #fff; /* 占位背景 */
}

.app-logo:hover {
  transform: scale(1.05) rotate(2deg);
}

.app-title {
  color: #1890ff !important; /* 强制覆盖AntD颜色 */
  margin-top: 24px !important;
  font-weight: 800 !important;
  font-size: 36px !important;
  letter-spacing: -0.5px;
}

.app-description {
  font-size: 18px;
  color: #666;
  max-width: 600px;
  margin: 16px auto 32px;
  line-height: 1.6;
}

.download-button {
  height: 56px;
  font-size: 18px;
  padding: 0 40px;
  border-radius: 28px;
  background: linear-gradient(135deg, #1890ff 0%, #36cfc9 100%);
  border: none;
  box-shadow: 0 8px 24px rgba(24, 144, 255, 0.35);
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
}

.download-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 32px rgba(24, 144, 255, 0.45);
}

/* =========================================
   3. 内容区域通用样式
   ========================================= */
.main-content {
  width: 100%;
  max-width: 1100px; /* 限制PC最大宽度 */
  padding: 0 20px 60px;
  position: relative;
  z-index: 1;
}

.section-block {
  margin-bottom: 60px;
}

/* 通用卡片样式 */
.content-card {
  border-radius: 24px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.6);
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(20px);
}

/* 标题装饰线 */
.section-title {
  text-align: center;
  margin-bottom: 30px !important;
  position: relative;
}

.section-title::after {
  content: '';
  display: block;
  width: 60px;
  height: 4px;
  background: linear-gradient(90deg, #1890ff 0%, #36cfc9 100%);
  margin: 16px auto 0;
  border-radius: 2px;
}

.intro-description {
  text-align: center;
  font-size: 16px;
  line-height: 1.8;
  color: #555;
  margin-bottom: 40px !important;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

/* =========================================
   4. 功能网格 (Features)
   ========================================= */
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 24px;
  margin-bottom: 40px;
}

.feature-card {
  height: 100%;
  background: #fff;
  border-radius: 16px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(0,0,0,0.02);
  flex:1;
}

.feature-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 30px rgba(0,0,0,0.08);
}

.feature-title {
  font-size: 18px;
  font-weight: 700;
  color: #1f1f1f;
  margin-bottom: 12px;
}

.feature-description {
  color: #666;
  font-size: 14px;
  line-height: 1.6;
  margin: 0;
}

/* 统计数据 */
.plugin-stats {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 20px;
  background: linear-gradient(135deg, #f0f9ff 0%, #e6f7ff 100%);
  border-radius: 16px;
  padding: 30px 20px;
  margin-top: 40px;
}

.stat-item {
  text-align: center;
  flex: 1;
  min-width: 140px;
}

.stat-number {
  display: block;
  font-size: 32px;
  font-weight: 800;
  color: #1890ff;
  font-family: Arial, sans-serif;
  margin-bottom: 8px;
}

.stat-label {
  color: #666;
  font-size: 14px;
  font-weight: 500;
}

/* =========================================
   5. 步骤指南 (Steps)
   ========================================= */
.steps-container {
  padding: 20px;
}

.step-item {
  display: flex;
  gap: 24px;
}

.step-number {
  flex-shrink: 0;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: linear-gradient(135deg, #1890ff 0%, #36cfc9 100%);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  font-weight: 700;
  box-shadow: 0 8px 20px rgba(24, 144, 255, 0.25);
}

.step-content {
  flex: 1;
}

.step-title {
  font-size: 20px;
  font-weight: 600;
  color: #1f1f1f;
  margin-bottom: 12px;
}

.step-description ol {
  padding-left: 20px;
  margin: 0;
  color: #555;
  line-height: 1.8;
}

.step-description li {
  margin-bottom: 8px;
}

.step-description code {
  background: #f5f5f5;
  border: 1px solid #d9d9d9;
  padding: 2px 6px;
  border-radius: 4px;
  color: #eb2f96;
  font-family: monospace;
}

.tip-text {
  background: #e6f7ff;
  border: 1px solid #91d5ff;
  padding: 12px 16px;
  border-radius: 8px;
  margin-top: 16px;
  color: #0050b3;
  font-size: 14px;
}

.step-divider {
  width: 2px;
  height: 40px;
  background: #e8e8e8;
  margin: 8px 0 8px 23px; /* 对齐圆圈中心 */
}

/* =========================================
   6. 版本历史 (Timeline)
   ========================================= */
.version-timeline {
  padding: 10px 20px;
}

.version-item {
  padding-bottom: 30px;
  border-bottom: 1px solid #f0f0f0;
  margin-bottom: 30px;
}

.version-item:last-child {
  border-bottom: none;
  margin-bottom: 0;
  padding-bottom: 0;
}

.version-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.version-badge {
  background: #f0f2f5;
  color: #595959;
  padding: 4px 12px;
  border-radius: 100px;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

.version-badge.latest {
  background: #e6f7ff;
  color: #1890ff;
  border: 1px solid #91d5ff;
}

.latest-badge {
  background: #1890ff;
  color: white;
  font-size: 12px;
  padding: 1px 6px;
  border-radius: 4px;
  line-height: 1.2;
}

.version-date {
  color: #999;
  font-size: 14px;
}

.change-item {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 8px;
  line-height: 1.6;
  color: #555;
}

.change-icon {
  color: #52c41a;
  margin-top: 3px;
}

/* =========================================
   7. Footer
   ========================================= */
.footer-section {
  padding: 0 20px 40px;
  text-align: center;
  color: #999;
  position: relative;
  z-index: 1;
}

/* =========================================
   8. 响应式适配
   ========================================= */
@media (max-width: 768px) {
  .app-title {
    font-size: 28px !important;
  }
  
  .header-section {
    padding-top: 40px;
  }
  
  .features-grid {
    grid-template-columns: 1fr;
  }
  
  .plugin-stats {
    flex-direction: column;
    gap: 30px;
  }
  
  .step-item {
    flex-direction: column;
    gap: 12px;
  }
  
  .step-divider {
    display: none;
  }
  
  .version-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 8px;
  }
}
</style>