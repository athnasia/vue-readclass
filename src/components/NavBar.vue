<script setup lang="ts">
import { RouterLink, useRoute } from 'vue-router'
import { Menu, Drawer, Button } from 'ant-design-vue'
import { BookOutlined, ReadOutlined, FileTextOutlined, EditOutlined, MenuOutlined } from '@ant-design/icons-vue'
import { computed, ref } from 'vue'

const menuItems = [
    { key: 'materials', icon: BookOutlined, label: '六维素材库', path: '/materials' },
    { key: 'textbook', icon: ReadOutlined, label: '教材精读', path: '/textbook' },
    { key: 'exam', icon: FileTextOutlined, label: '应试阅读', path: '/exam' },
    { key: 'writing', icon: EditOutlined, label: '写作微技巧', path: '/writing' }
]

const route = useRoute()
const selectedKey = computed(() => {
    if (route.path === '/') return 'home'
    if (route.path.startsWith('/materials')) return 'materials'
    if (route.path.startsWith('/textbook')) return 'textbook'
    if (route.path.startsWith('/exam')) return 'exam'
    if (route.path.startsWith('/writing')) return 'writing'
    if (route.path.startsWith('/about')) return 'about'
    return ''
})

// 移动端抽屉控制
const mobileMenuVisible = ref(false)

const showMobileMenu = () => {
    mobileMenuVisible.value = true
}

const hideMobileMenu = () => {
    mobileMenuVisible.value = false
}
</script>

<template>
    <header class="header">
        <div class="logo">
            <img alt="Vue logo" src="@/assets/logo.svg" width="32" height="32" />
            <span class="logo-text">唐老师的高阶阅读课</span>
        </div>
        
        <!-- 桌面端导航菜单 -->
        <Menu mode="horizontal" :selected-keys="[selectedKey]" class="nav-menu desktop-menu">
            <Menu.Item key="home">
                <RouterLink to="/">首页</RouterLink>
            </Menu.Item>
            <Menu.Item v-for="item in menuItems" :key="item.key">
                <RouterLink :to="item.path">
                    <component :is="item.icon" />
                    <span class="nav-label">{{ item.label }}</span>
                </RouterLink>
            </Menu.Item>
            <Menu.Item key="about">
                <RouterLink to="/about">关于</RouterLink>
            </Menu.Item>
        </Menu>
        
        <!-- 移动端菜单按钮 -->
        <Button 
            type="text" 
            class="mobile-menu-btn"
            @click="showMobileMenu"
        >
            <MenuOutlined />
        </Button>
        
        <!-- 移动端抽屉菜单 -->
        <Drawer
            title="导航菜单"
            placement="right"
            :visible="mobileMenuVisible"
            @close="hideMobileMenu"
            class="mobile-drawer"
        >
            <Menu 
                mode="vertical" 
                :selected-keys="[selectedKey]"
                @click="hideMobileMenu"
            >
                <Menu.Item key="home">
                    <RouterLink to="/">首页</RouterLink>
                </Menu.Item>
                <Menu.Item v-for="item in menuItems" :key="item.key">
                    <RouterLink :to="item.path">
                        <component :is="item.icon" />
                        <span class="nav-label">{{ item.label }}</span>
                    </RouterLink>
                </Menu.Item>
                <Menu.Item key="about">
                    <RouterLink to="/about">关于</RouterLink>
                </Menu.Item>
            </Menu>
        </Drawer>
    </header>
</template>

<style scoped>
.header {
    display: flex;
    align-items: center;
    background: #fff;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    padding: 0 24px;
    width: 100vw;
    box-sizing: border-box;
    position: relative;
}

.logo {
    display: flex;
    align-items: center;
    margin-right: 48px;
    flex-shrink: 0;
}

.logo img {
    margin-right: 8px;
}

.logo-text {
    font-size: 18px;
    font-weight: bold;
    color: #1890ff;
}

.nav-menu {
    flex: 1;
    border-bottom: none;
    font-size: 20px;
    font-weight: bold;
}

.nav-menu :deep(.ant-menu-item) {
    display: flex;
    align-items: center;
    padding: 0 16px;
}

.nav-menu :deep(.ant-menu-item a) {
    display: flex;
    align-items: center;
    color: inherit;
    text-decoration: none;
}

.nav-label {
    margin-left: 8px;
}

/* 强力覆盖 Antd Menu 悬停和选中背景色 */
:deep(.ant-menu-horizontal > .ant-menu-item:hover),
:deep(.ant-menu-horizontal > .ant-menu-item-active),
:deep(.ant-menu-horizontal > .ant-menu-item-selected),
:deep(.ant-menu-horizontal > .ant-menu-item-selected:hover),
:deep(.ant-menu-horizontal > .ant-menu-submenu-selected),
:deep(.ant-menu-horizontal > .ant-menu-submenu-active),
:deep(.ant-menu-horizontal > .ant-menu-submenu-title:hover) {
    background: transparent !important;
    background-color: transparent !important;
}

/* 移动端样式 */
.mobile-menu-btn {
    display: none;
    font-size: 20px;
    color: #1890ff;
    border: none;
    padding: 8px;
    height: auto;
}

.mobile-drawer :deep(.ant-drawer-header) {
    background: #fafdff;
    border-bottom: 1px solid #e8f4ff;
}

.mobile-drawer :deep(.ant-drawer-body) {
    padding: 0;
    background: #fafdff;
}

.mobile-drawer :deep(.ant-menu-vertical) {
    border-right: none;
    background: transparent;
}

.mobile-drawer :deep(.ant-menu-item) {
    margin: 0;
    padding: 16px 24px;
    border-bottom: 1px solid #e8f4ff;
    font-size: 16px;
    font-weight: 500;
}

.mobile-drawer :deep(.ant-menu-item a) {
    display: flex;
    align-items: center;
    color: #333;
    text-decoration: none;
}

.mobile-drawer :deep(.ant-menu-item-selected) {
    background: #e6f7ff !important;
    color: #1890ff !important;
}

.mobile-drawer :deep(.ant-menu-item-selected a) {
    color: #1890ff !important;
}

/* 响应式断点 */
@media (max-width: 768px) {
    .header {
        padding: 0 16px;
    }
    
    .logo {
        margin-right: 16px;
    }
    
    .logo-text {
        font-size: 16px;
    }
    
    .desktop-menu {
        display: none;
    }
    
    .mobile-menu-btn {
        display: block;
    }
}

@media (max-width: 480px) {
    .header {
        padding: 0 12px;
    }
    
    .logo-text {
        font-size: 14px;
    }
    
    .logo img {
        width: 28px;
        height: 28px;
    }
}
</style>