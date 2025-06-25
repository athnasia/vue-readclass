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

function onSelect(keys: string[], { node }: { node: TreeNode }) {
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
        <Row :gutter="0" align="top" justify="start" class="material-layout">
            <Col class="tree-col">
            <a-tree :tree-data="treeData" :expanded-keys="expandedKeys" :selected-keys="selectedKeys"
                :expandAction="'click'" @select="onSelect" @expand="onExpand" />
            </Col>
            <Col flex="1" class="table-col">
            <a-breadcrumb style="margin-bottom:16px">
                <a-breadcrumb-item v-for="(item, idx) in breadcrumb" :key="idx">{{ item }}</a-breadcrumb-item>
            </a-breadcrumb>
            <div class="table-container">
                <a-table :columns="columns" :data-source="dataSource" bordered />
            </div>
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

.material-layout {
    width: 100%;
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

.table-container {
    overflow-x: auto;
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

/* 移动端适配 */
@media (max-width: 768px) {
    .material-root {
        padding: 16px 0 0 0;
    }
    
    .material-layout {
        flex-direction: column;
    }
    
    .tree-col {
        width: 100% !important;
        margin: 0 16px 16px 16px;
        padding: 20px 16px;
        min-height: auto;
        border-radius: 8px;
    }
    
    .table-col {
        margin: 0 16px 16px 16px;
        padding: 20px 16px;
        min-height: auto;
        border-radius: 8px;
    }
    
    .table-container {
        overflow-x: auto;
        -webkit-overflow-scrolling: touch;
    }
    
    :deep(.ant-breadcrumb) {
        font-size: 14px;
        margin-bottom: 16px;
    }
    
    :deep(.ant-table) {
        font-size: 14px;
    }
    
    :deep(.ant-table-thead > tr > th) {
        padding: 8px 4px;
        font-size: 13px;
    }
    
    :deep(.ant-table-tbody > tr > td) {
        padding: 8px 4px;
        font-size: 13px;
    }
    
    :deep(.ant-tree) {
        font-size: 14px;
    }
    
    :deep(.ant-tree-node-content-wrapper) {
        padding: 6px 8px;
    }
}

@media (max-width: 480px) {
    .material-root {
        padding: 12px 0 0 0;
    }
    
    .tree-col {
        margin: 0 12px 12px 12px;
        padding: 16px 12px;
        border-radius: 6px;
    }
    
    .table-col {
        margin: 0 12px 12px 12px;
        padding: 16px 12px;
        border-radius: 6px;
    }
    
    :deep(.ant-breadcrumb) {
        font-size: 12px;
        margin-bottom: 12px;
    }
    
    :deep(.ant-table) {
        font-size: 12px;
    }
    
    :deep(.ant-table-thead > tr > th) {
        padding: 6px 2px;
        font-size: 11px;
    }
    
    :deep(.ant-table-tbody > tr > td) {
        padding: 6px 2px;
        font-size: 11px;
    }
    
    :deep(.ant-tree) {
        font-size: 12px;
    }
    
    :deep(.ant-tree-node-content-wrapper) {
        padding: 4px 6px;
    }
}

/* 超小屏幕适配 */
@media (max-width: 360px) {
    .tree-col {
        margin: 0 8px 8px 8px;
        padding: 12px 8px;
    }
    
    .table-col {
        margin: 0 8px 8px 8px;
        padding: 12px 8px;
    }
    
    :deep(.ant-breadcrumb) {
        font-size: 11px;
        margin-bottom: 8px;
    }
    
    :deep(.ant-table) {
        font-size: 11px;
    }
    
    :deep(.ant-table-thead > tr > th) {
        padding: 4px 1px;
        font-size: 10px;
    }
    
    :deep(.ant-table-tbody > tr > td) {
        padding: 4px 1px;
        font-size: 10px;
    }
    
    :deep(.ant-tree) {
        font-size: 11px;
    }
    
    :deep(.ant-tree-node-content-wrapper) {
        padding: 3px 4px;
    }
}
</style>