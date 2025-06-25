<script setup lang="ts">
import { ref, computed } from 'vue'
import { Row, Col } from 'ant-design-vue'

interface TreeNode {
    title: string;
    key: string;
    children?: TreeNode[];
}

const treeData: TreeNode[] = [
    {
        title: '情感', key: 'emotion',
        children: [
            {
                title: '句', key: 'emotion-1-1',
                children: [
                    { title: '传世名言', key: 'emotion-1-1-1' },
                    { title: '当下热句', key: 'emotion-1-1-2' }
                ]
            },
            {
                title: '段', key: 'emotion-1-2',
                children: [
                    { title: '经典语段', key: 'emotion-1-2-1' },
                    { title: '热文选段', key: 'emotion-1-2-2' }
                ]
            },
            {
                title: '篇', key: 'emotion-1-3',
                children: [
                    { title: '经典美文', key: 'emotion-1-3-1' },
                    { title: '时文推荐', key: 'emotion-1-3-2' }
                ]
            }
        ]
    },
    {
        title: '理性', key: 'reason',
        children: [
            {
                title: '句', key: 'reason-1-1',
                children: [
                    { title: '传世名言', key: 'reason-1-1-1' },
                    { title: '当下热句', key: 'reason-1-1-2' }
                ]
            },
            {
                title: '段', key: 'reason-1-2',
                children: [
                    { title: '经典语段', key: 'reason-1-2-1' },
                    { title: '热文选段', key: 'reason-1-2-2' }
                ]
            },
            {
                title: '篇', key: 'reason-1-3',
                children: [
                    { title: '经典美文', key: 'reason-1-3-1' },
                    { title: '时文推荐', key: 'reason-1-3-2' }
                ]
            }
        ]
    },
    {
        title: '认知', key: 'cognition',
        children: [
            {
                title: '句', key: 'cognition-1-1',
                children: [
                    { title: '传世名言', key: 'cognition-1-1-1' },
                    { title: '当下热句', key: 'cognition-1-1-2' }
                ]
            },
            {
                title: '段', key: 'cognition-1-2',
                children: [
                    { title: '经典语段', key: 'cognition-1-2-1' },
                    { title: '热文选段', key: 'cognition-1-2-2' }
                ]
            },
            {
                title: '篇', key: 'cognition-1-3',
                children: [
                    { title: '经典美文', key: 'cognition-1-3-1' },
                    { title: '时文推荐', key: 'cognition-1-3-2' }
                ]
            }
        ]
    },
    {
        title: '道义', key: 'morality',
        children: [
            {
                title: '句', key: 'morality-1-1',
                children: [
                    { title: '传世名言', key: 'morality-1-1-1' },
                    { title: '当下热句', key: 'morality-1-1-2' }
                ]
            },
            {
                title: '段', key: 'morality-1-2',
                children: [
                    { title: '经典语段', key: 'morality-1-2-1' },
                    { title: '热文选段', key: 'morality-1-2-2' }
                ]
            },
            {
                title: '篇', key: 'morality-1-3',
                children: [
                    { title: '经典美文', key: 'morality-1-3-1' },
                    { title: '时文推荐', key: 'morality-1-3-2' }
                ]
            }
        ]
    },
    {
        title: '智慧', key: 'wisdom',
        children: [
            {
                title: '句', key: 'wisdom-1-1',
                children: [
                    { title: '传世名言', key: 'wisdom-1-1-1' },
                    { title: '当下热句', key: 'wisdom-1-1-2' }
                ]
            },
            {
                title: '段', key: 'wisdom-1-2',
                children: [
                    { title: '经典语段', key: 'wisdom-1-2-1' },
                    { title: '热文选段', key: 'wisdom-1-2-2' }
                ]
            },
            {
                title: '篇', key: 'wisdom-1-3',
                children: [
                    { title: '经典美文', key: 'wisdom-1-3-1' },
                    { title: '时文推荐', key: 'wisdom-1-3-2' }
                ]
            }
        ]
    },
    {
        title: '情趣', key: 'interest',
        children: [
            {
                title: '句', key: 'interest-1-1',
                children: [
                    { title: '传世名言', key: 'interest-1-1-1' },
                    { title: '当下热句', key: 'interest-1-1-2' }
                ]
            },
            {
                title: '段', key: 'interest-1-2',
                children: [
                    { title: '经典语段', key: 'interest-1-2-1' },
                    { title: '热文选段', key: 'interest-1-2-2' }
                ]
            },
            {
                title: '篇', key: 'interest-1-3',
                children: [
                    { title: '经典美文', key: 'interest-1-3-1' },
                    { title: '时文推荐', key: 'interest-1-3-2' }
                ]
            }
        ]
    }
]

const columns = [
    { title: '标题', dataIndex: 'title', key: 'title' },
    { title: '详细', dataIndex: 'detail', key: 'detail' },
    { title: '鉴赏', dataIndex: 'appreciation', key: 'appreciation' },
    { title: '功能', dataIndex: 'action', key: 'action' }
]

// mock 数据，key为树节点key
const allData = [
    { key: 'emotion-1-1-1', title: '情感-传世名言1', detail: '内容A', appreciation: '鉴赏A', action: '功能A' },
    { key: 'emotion-1-1-2', title: '情感-当下热句1', detail: '内容B', appreciation: '鉴赏B', action: '功能B' },
    { key: 'reason-1-1-1', title: '理性-传世名言1', detail: '内容C', appreciation: '鉴赏C', action: '功能C' },
    { key: 'wisdom-1-2-1', title: '智慧-经典语段1', detail: '内容D', appreciation: '鉴赏D', action: '功能D' },
    // ...可继续扩展
]

const selectedKeys = ref(['emotion-1-1-1'])
const expandedKeys = ref(['emotion', 'emotion-1-1'])

function onExpand(keys: string[]) {
    expandedKeys.value = keys
}

function onSelect(keys: string[], { node }: { node: any }) {
    // 只有叶子节点才切换选中
    if (!node.children || node.children.length === 0) {
        selectedKeys.value = keys
    }
}

// 递归查找面包屑路径
function findPathByKey(tree: TreeNode[], key: string, path: string[] = []): string[] | null {
    for (const node of tree) {
        const newPath = [...path, node.title]
        if (node.key === key) return newPath
        if (node.children) {
            const childPath = findPathByKey(node.children, key, newPath)
            if (childPath) return childPath
        }
    }
    return null
}
const breadcrumb = computed(() => {
    const key = selectedKeys.value[0]
    if (!key) return []
    return findPathByKey(treeData, key) || []
})

// 表格数据联动
const dataSource = computed(() => {
    const key = selectedKeys.value[0]
    if (!key) return []
    // 递归获取所有子孙key
    function getAllKeys(tree: TreeNode[], targetKey: string): string[] {
        for (const node of tree) {
            if (node.key === targetKey) {
                return collectKeys(node)
            }
            if (node.children) {
                const found = getAllKeys(node.children, targetKey)
                if (found.length) return found
            }
        }
        return []
    }
    function collectKeys(node: TreeNode): string[] {
        let keys = [node.key]
        if (node.children) {
            for (const child of node.children) {
                keys = keys.concat(collectKeys(child))
            }
        }
        return keys
    }
    const keys = getAllKeys(treeData, key)
    return allData.filter(item => keys.includes(item.key))
})
</script>

<template>
    <div class="material-root">
        <Row :gutter="0" align="top" justify="start">
            <Col class="tree-col">
            <a-tree :tree-data="treeData" :expanded-keys="expandedKeys" :selected-keys="selectedKeys"
                :expandAction="'click'" @select="onSelect" @expand="onExpand" />
            </Col>
            <Col flex="1" class="table-col">
            <a-breadcrumb style="margin-bottom:16px">
                <a-breadcrumb-item v-for="(item, idx) in breadcrumb" :key="idx">{{ item }}</a-breadcrumb-item>
            </a-breadcrumb>
            <a-table :columns="columns" :data-source="dataSource" bordered />
            </Col>
        </Row>
    </div>
</template>

<style scoped>
.material-root {
    width: 100vw;
    min-height: 80vh;
    background: #fafdff;
    padding: 32px 0 0 0;
    box-sizing: border-box;
}

.tree-col {
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 4px 16px rgba(24, 144, 255, 0.06);
    padding: 32px 16px;
    min-height: 600px;
    margin-left: 32px;
    margin-right: 24px;
    width: 260px;
}

.table-col {
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 4px 16px rgba(24, 144, 255, 0.06);
    padding: 32px 32px;
    min-height: 600px;
    margin-right: 32px;
}

:deep(.ant-tree .ant-tree-node-content-wrapper.ant-tree-node-selected) {
    background: #e6f7ff !important;
    color: #1890ff !important;
    font-weight: bold;
}

:deep(.ant-tree .ant-tree-node-content-wrapper:hover) {
    background: #f0f7ff !important;
}

:deep(.ant-breadcrumb) {
    font-size: 18px;
    font-weight: 500;
    margin-bottom: 24px;
}

:deep(.ant-table-tbody > tr:hover > td) {
    background: #f0f7ff !important;
}

:deep(.ant-table) {
    font-size: 16px;
}
</style>