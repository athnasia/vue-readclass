<script setup lang="ts">
import { RouterLink, useRoute } from 'vue-router'
import { Menu } from 'ant-design-vue'
import { BookOutlined, ReadOutlined, FileTextOutlined, EditOutlined } from '@ant-design/icons-vue'
import { computed } from 'vue'

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
</script>

<template>
    <header class="header">
        <div class="logo">
            <img alt="Vue logo" src="@/assets/logo.svg" width="32" height="32" />
            <span class="logo-text">唐老师的高阶阅读课</span>
        </div>
        <Menu mode="horizontal" :selected-keys="[selectedKey]" class="nav-menu">
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
}

.logo {
    display: flex;
    align-items: center;
    margin-right: 48px;
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
</style>